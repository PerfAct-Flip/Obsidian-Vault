## Linked Note
[[zustand stores]]


Good — now this is the **right question**.

I’ll give you **only variable names**, grouped logically, with **zero implementation detail**.  
These names reflect the mental model you’ve already accepted.

---

## 1️⃣ Core Project Data (Story Truth)

### Nodes

- `nodes`
    
- `nodeTypes`
    

Each node should conceptually have:

- `id`
    
- `type`
    
- `startTime`
    
- `endTime`
    
- `position`
    

(You asked for variable names, so the store variable is just `nodes`.)

---

### Relationships

- `relationships`
    
- `relationshipTypes`
    

Each relationship conceptually references:

- `id`
    
- `type`
    
- `fromNodeId`
    
- `toNodeId`
    
- `startTime`
    
- `endTime`
    

---

## 2️⃣ Timeline State (Critical, but Separate)

- `currentTime`
    
- `timelineState` _(play | pause)_
    
- `timelineStart`
    
- `timelineEnd`
    

---

## 3️⃣ Selection & Interaction State

- `selectedNodeId`
    
- `selectedRelationshipId`
    
- `hoveredNodeId`
    
- `hoveredRelationshipId`
    

---

## 4️⃣ Canvas / View State (Not Story Data)

- `zoomLevel`
    
- `panX`
    
- `panY`
    

---

## 5️⃣ UI Coordination (Ephemeral)

- `activeTool`  
    _(select | addNode | addRelationship | delete)_
    
- `isDragging`
    
- `isScrubbingTimeline`
    

---

## 6️⃣ Persistence (Local-only for now)

- `projectId`
    
- `lastSavedAt`
    

---

## What Is **Deliberately Missing**

Notice what I did **not** include:

- ❌ `visibleNodes`
    
- ❌ `visibleRelationships`
    
- ❌ `filteredNodes`
    
- ❌ `renderNodes`
    

Those are **derived**, not stored.

---

## One Rule You Must Obey

> **If a variable can be computed from other variables, it does NOT belong in the store.**

Breaking this rule is how apps become unmaintainable.

---

## Your Next Step (Do This Alone)

Take these names and:

1. Write them on paper
    
2. Draw arrows:
    
    - Which affect timeline?
        
    - Which affect rendering?
        
    - Which affect story truth?
        

If you can do that without guessing, you’re building the right thing.

When you’re ready, bring **one group** (only one) and ask:

> “Are these responsibilities clean?”

I’ll validate — not redesign.