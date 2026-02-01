## Linked Note
[[ChronoCanvas (Working Title)]]


# Define “Persistence Operations” (Conceptual API)

Before writing code, decide the **verbs** your DB supports.

Examples:

- `createNode`
    
- `updateNode`
    
- `endNode`
    
- `deleteNode`
    
- `createRelationship`
    
- `endRelationship`
    
- `deleteRelationship`
    
- `loadAllNodes`
    
- `loadAllRelationships`
    

Zustand will call these — not the UI.



# Sync Strategy with Zustand (Critical)

Decide **who initiates sync**:

### Recommended:

- On app start → load everything from Dexie into Zustand
    
- On mutation → write to Dexie, then update Zustand
    

Never:

- Read Dexie directly inside React components
    
- Let Zustand silently diverge from Dexie

# Failure & Delay Acceptance (You Already Did This Right)

You already said:

> “I’m fine with 1–2 sec delays”

So:

- Dexie writes can be async
    
- UI can show pending state
    
- Timeline logic remains deterministic
    

This is a **good constraint**, not a weakness.