## Linked Note
[[ChronoCanvas (Working Title)]]
Got it — **no code**. I’ll explain **what you need to do with Zustand**, conceptually and structurally, so you know _why_ and _where_ it fits.

---

## What Zustand’s Role Is in Your App

Zustand is the **single source of truth** for anything that must be shared between:

- Canvas
    
- Timeline
    
- Side panels
    
- Persistence (IndexedDB)
    

Think of Zustand as the **brain** of the editor.

---

## What Should Live in Zustand (and Why)

### 1️⃣ Timeline State (Critical)

**What**

- Current time
    
- Timeline length
    
- Play / pause state
    

**Why**

- Canvas visibility depends on time
    
- Timeline slider updates many components
    
- Needs fast, global updates
    

This is **non-negotiable global state**.

---

### 2️⃣ Core Project Data

**What**

- Nodes
    
- Relationships
    
- Node types
    
- Relationship types
    
- Project metadata (name, duration)
    

**Why**

- Shared across canvas + panels
    
- Must persist locally
    
- Must be editable from multiple UI locations
    

This is your **domain state**.

---

### 3️⃣ Selection & UI Coordination State

**What**

- Currently selected node / relationship
    
- Hovered element (optional)
    
- Active tool (select, connect, pan)
    

**Why**

- Canvas interactions affect panels
    
- Panels affect canvas rendering
    
- Needs coordination, not prop passing
    

---

### 4️⃣ Editor Behavior State (Lightweight)

**What**

- Snap-to-grid on/off
    
- Ghost mode on/off
    
- Visibility toggles
    

**Why**

- Affects rendering globally
    
- Doesn’t belong in components
    

---

## What Should NOT Live in Zustand

❌ Canvas internal refs  
❌ Konva stage instance  
❌ Local hover animations  
❌ Temporary drag positions

Rule:

> If it dies on refresh → keep it local  
> If it defines the project → put it in Zustand

---

## How You Should Organize Zustand Conceptually

### One Store, Logical Sections

Not multiple stores. One store with **clear sections**:

- Timeline
    
- Project data
    
- Selection
    
- Editor settings
    
- Actions (mutations)
    

This keeps everything coherent.

---

## How Zustand Interacts With Other Parts

### Canvas

- Reads visible nodes based on time
    
- Writes node position updates
    
- Updates selection
    

### Timeline

- Updates current time
    
- Triggers visibility recalculation
    

### Properties Panel

- Reads selected element
    
- Writes edits to nodes/edges
    

### Persistence Layer

- Listens to store changes
    
- Saves snapshots to IndexedDB
    

Zustand sits **between UI and storage**.

---

## How to Think About Updates (Very Important)

You should think in terms of **intent**, not UI events.

Bad mental model:

> “User dragged a node”

Good mental model:

> “Node position updated”

Zustand handles **domain actions**, not UI mechanics.

---

## Timeline Scrubbing Rule (Key Insight)

When time changes:

- **Do NOT mutate nodes**
    
- **Do NOT add/remove data**
    
- Only change `currentTime`
    
- Rendering layer decides what’s visible
    

This keeps the system stable and debuggable.

---

## Why Zustand Helps Long-Term

- Easy to add undo/redo later
    
- Easy to sync to backend later
    
- Easy to add version snapshots
    
- Easy to add collaboration later
    

Because all logic flows through one state system.

---

## What You Need to “Do” With Zustand (Checklist)

- Decide global state shape
    
- Decide which actions mutate that state
    
- Ensure all major UI parts read from it
    
- Ensure persistence listens to it
    
- Keep UI components mostly stateless
    

That’s it.

---

## Final Mental Model

> **Zustand = authoritative project state + editor coordination**

Not UI state.  
Not storage.  
The _truth_.

---

If you want next, I can:

- Explain **undo/redo strategy**
    
- Explain **timeline + state performance**
    
- Explain **how to future-proof for sync**
    
- Explain **testing strategy for state**
    

Just tell me.
