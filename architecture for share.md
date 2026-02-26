To implement a basic invitation mechanism with Role-Based Access Control (RBAC) as you described, you will need to modify both the data handling in your context and the UI components to enforce restrictions.

Since you requested a description of what should be done without execution, here is the architectural plan:

### 1. Extend the Data Model & Auth Context

The UI needs to know the "Role" of the current user relative to the selected agent. You should update your 

```
AuthContext
```

 to determine and expose this role.

- **Update 
    
    ```
    AuthContext
    ```
    
    **: In 
    
    src/components/rag/dashboard/AuthContext.tsx, add a 
    
    ```
    role
    ```
    
     field to the context value.
- **Role Logic**:
    - **Owner**: If 
        
        ```
        profile.email === selectedAgent.owner_id
        ```
        
        .
    - **Editor/Viewer**: Inherit this from the backend response when fetching the agent details or via a separate "members" endpoint.
- **New Type**: Define the hierarchy in 
    
    src/types/invitations.ts:
    
    typescript
    
    export type UserRole = "owner" | "editor" | "viewer";
    

### 2. Implement a Permissions Hook

Create a utility hook 

```
usePermission
```

 to centralize logic for what users can do. This makes the UI code cleaner and easier to maintain.

- **File**: 
    
    ```
    src/hooks/usePermission.ts
    ```
    
- **Logic**:
    
    typescript
    
    const permissions = {
    
      owner: ['manage_services', 'invite_users', 'edit_config', 'chat'],
    
      editor: ['edit_config', 'chat'],
    
      viewer: ['view_config', 'chat']
    
    }
    

### 3. Update the "Share Agent" UI

The user invitation UI is located in 

```
src/app/dashboard/share-agent
```

.

- **Invite Section**: Add a dropdown to 
    
    ```
    InviteUsersSection
    ```
    
     allowing the Owner to select "Viewer" or "Editor" for the new invitee.
- **Users List**: Update 
    
    ```
    InvitedUsersList
    ```
    
     to display the role of each user and allow the Owner to change it or revoke access.
- **Owner-Only Gate**: Wrap individual sections of this page so only the 
    
    ```
    owner
    ```
    
     can see the invitation inputs. Non-owners might only see a list of team members.

### 4. Enforce "Owner-Only" Service Management

The core requirement is that only owners can enable/disable services.

- **Integration Services**: In 
    
    ```
    src/components/rag/dashboard/IntegrationServices.tsx
    ```
    
    , update the action buttons:
    - **Connect/Disconnect**: Wrap these in a check. If 
        
        ```
        role !== 'owner'
        ```
        
        , hide the buttons or replace them with a "Permissions Required" tooltip.
    - **Edit Integration**: Allow 
        
        ```
        editor
        ```
        
         and 
        
        ```
        owner
        ```
        
         to access the configuration edit screen, but only allow 
        
        ```
        owner
        ```
        
         to actually toggle the service "Status" (enabled/disabled).
- **Service Toggles**: Any UI switch or button that calls 
    
    ```
    deleteServiceFromAgent
    ```
    
     or an "enable" endpoint must be restricted to the 
    
    ```
    owner
    ```
    
     role.

### 5. UI/UX Feedback

To ensure a premium feel and clear communication:

- **Visual Indicators**: Add a small badge (e.g., "Owner", "Editor") next to the user's profile or in the Agent header so they know their current permissions.
- **Restricted State**: Instead of just hiding buttons, consider showing them in a "disabled" state with a tooltip like: _"Only the Agent Owner can enable or disable this service."_
- **Sidebar/Navigation**: Hide the "Share Agent" and "Billing/Limits" links from the sidebar if the user is not an 
    
    ```
    owner
    ```
    
    .

### Summary of Component Changes:

1. **
    
    ```
    AuthContext.tsx
    ```
    
    **: Add 
    
    ```
    currentRole
    ```
    
     to the context.
2. **
    
    ```
    IntegrationServices.tsx
    ```
    
    **: Add 
    
    ```
    role
    ```
    
     check to 
    
    ```
    Connect
    ```
    
     and 
    
    ```
    Disconnect
    ```
    
     buttons.
3. **
    
    ```
    InviteUsersSection.tsx
    ```
    
    **: Add Role selection logic.
4. **
    
    ```
    InvitedUsersList.tsx
    ```
    
    **: Add Role display and management (for owners).

By following this plan, you will maintain a strict "Owner-Only" policy for service management while allowing team collaboration for usage and configuration.








--- 
To start working, you should follow this sequence to set up the foundation first. This allows you to then "lock down" the UI based on the user's role.

### **Step 1: Define the Roles**

Open 

**src/types/invitations.ts** and ensure your roles are clearly defined. You already have some, but let's make sure they match your requirements:

typescript

// Add or update these to match your logic

export type InvitationRole = "owner" | "editor" | "viewer";

---

### **Step 2: Update the Auth Context**

Modify 

**src/components/rag/dashboard/AuthContext.tsx** to calculate and export the current user's role. This is the "brain" of your permissions.

1. **Add 
    
    ```
    role
    ```
    
     to the context type**:
    
    typescript
    
    role: InvitationRole;
    
2. **Calculate the role** (inside 
    
    AuthProvider):
    
    typescript
    
    const role = useMemo((): InvitationRole => {
    
      if (profile?.email === selectedAgent?.owner_id) return "owner";
    
      // This part would eventually come from the backend for invited users
    
      // For now, default to "viewer" or "editor" based on your testing needs
    
      return (selectedAgent as any)?.current_user_role || "viewer";
    
    }, [profile, selectedAgent]);
    

---

### **Step 3: Create a Permissions Hook**

Create a new file 

**`src/hooks/usePermission.ts`**

. This will be your primary way to check if a user can do something (like enable a service).

typescript

import { useAuth } from "./useAuth";

export const usePermission = () => {

  const { role } = useAuth();

  return {

    role,

    isOwner: role === "owner",

    isEditor: role === "editor",

    isViewer: role === "viewer",

    canManageServices: role === "owner", // ONLY Owner

    canEditConfig: role === "owner" || role === "editor",

    canInvite: role === "owner",

  };

};

---

### **Step 4: Lock the Service Toggles**

Now you can actually use the permissions. Open 

**src/components/rag/dashboard/IntegrationServices.tsx** and use your new hook to disable the "Disconnect" or "Connect" buttons for non-owners.

tsx

const { canManageServices } = usePermission();

// In your JSX for the Connect/Disconnect buttons:

<Button 

  disabled={!canManageServices} 

  title={!canManageServices ? "Only the owner can manage services" : ""}

  // ... other props

>

  Connect

</Button>

### **Where to start right now?**

Since you have 

```
InviteUsersSection.tsx
```

 open, I recommend starting with **Step 1 & 2** so that you can use the role inside your invitation UI to show/hide the "Invite" button or role dropdown.

**Would you like me to generate the exact code for the** 

**`AuthContext`**

 **update to get you rolling?**


![[Pasted image 20260225192017.png]]