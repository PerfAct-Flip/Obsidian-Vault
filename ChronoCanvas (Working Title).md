## Linked Note
[[Projects]]


Below is a **single, complete MVP roadmap + technical spec** you can directly follow. This is written as a **build document**, not theory.

---

### MVP Roadmap + Technical Specification

## 0. MVP Goal (One-Line)

Build a **local-first 2D temporal canvas** where creators place entities and relationships that **appear, disappear, and evolve over a timeline**.

---

## 1. MVP Feature Scope (Frozen)

### Included ✅

- Infinite **2D pan + zoom canvas**
    
- **Add / remove nodes**
    
- **Add / remove relationships**
    
- **User-defined node & relationship types**
    
- **Timeline scrubber**
    
- Nodes & edges **appear/disappear based on time**
    
- **Local persistence**
    

### Explicitly Excluded ❌

- Multi-user collaboration
    
- Cloud sync
    
- Auth
    
- Export formats
    
- AI features
    

(These come later.)

---

## 2. Technology Stack (Final)

### Frontend

- **React + TypeScript**
    
- **Canvas Engine:** `react-konva`
    
- **Animations:** `framer-motion`
    
- **State:** Zustand
    
- **Styling:** Tailwind CSS
    

### Storage

- **IndexedDB via Dexie.js** (local-first, async, scalable)
    

---

## 3. Core Data Model (Do Not Change Lightly)

### Node (Element)

```ts
type CanvasNode = {
  id: string
  name: string
  typeId: string
  x: number
  y: number
  startTime: number
  endTime: number | null
  meta?: Record<string, any>
}
```

### Relationship (Edge)

```ts
type Relationship = {
  id: string
  from: string
  to: string
  typeId: string
  startTime: number
  endTime: number | null
}
```

### Node Types

```ts
type NodeType = {
  id: string
  label: string
  color: string
  icon?: string
}
```

### Relationship Types

```ts
type RelationshipType = {
  id: string
  label: string
  style: "solid" | "dashed" | "arrow"
}
```

---

## 4. Default Types (Ship These)

### Node Types (5)

1. Character
    
2. Item
    
3. Location
    
4. Event
    
5. Faction
    

### Relationship Types (4)

1. Ally
    
2. Enemy
    
3. Owns
    
4. Appears In
    

Users can add/edit/delete types.

---

## 5. Timeline Rules (Deterministic)

A node or relationship is **visible at time `T`** if:

```ts
startTime <= T && (endTime === null || T <= endTime)
```

No exceptions. No hidden state.

---

## 6. Local Database Schema (Dexie)

```ts
db.version(1).stores({
  projects: "id",
  nodes: "id, startTime, endTime",
  relationships: "id, startTime, endTime",
  nodeTypes: "id",
  relationshipTypes: "id"
})
```

---

## 7. UI Layout (Simple & Effective)

```
-------------------------------------------------
| Top Bar: Project Name | Save | Reset | Help |
-------------------------------------------------
| Types Panel |        Canvas        | Properties |
|             |  (Pan + Zoom)        | Panel     |
|             |                      |           |
-------------------------------------------------
| Timeline Scrubber  ◄◄ ▶ ▶▶   Time |
-------------------------------------------------
```

---

## 8. Canvas Interaction Rules

### Canvas

- Drag → pan
    
- Scroll → zoom
    
- Click empty → deselect
    
- Right-click → context menu
    

### Nodes

- Click → select
    
- Drag → reposition
    
- Delete → removes node + related edges
    
- Properties panel:
    
    - Name
        
    - Type
        
    - Start / End time
        

### Relationships

- Create: select node A → node B
    
- Delete from properties or right-click
    

---

## 9. Timeline UX Behavior

- Drag scrubber → update visible graph
    
- Play button → auto-increment time
    
- Fade in/out:
    
    - Appearing: opacity 0 → 1
        
    - Disappearing: opacity 1 → 0.2 → remove
        

Optional: ghost mode toggle (future)

---

## 10. State Management Structure

```ts
{
  currentTime,
  nodes,
  relationships,
  nodeTypes,
  relationshipTypes,
  selectedElement
}
```

Timeline changes **never mutate data**, only filter visibility.

---

## 11. Development Roadmap (Step-by-Step)

### Phase 1 — Foundation (Day 1–2)

- Project setup (Vite + TS)
    
- Zustand store
    
- Dexie DB setup
    
- Basic layout
    

### Phase 2 — Canvas Core (Day 3–4)

- Konva stage
    
- Pan + zoom
    
- Render nodes
    
- Drag nodes
    

### Phase 3 — Relationships (Day 5)

- Draw edges
    
- Handle node deletion cascade
    

### Phase 4 — Timeline (Day 6)

- Scrubber
    
- Visibility filtering
    
- Play / pause
    

### Phase 5 — Types System (Day 7)

- Node/relationship types
    
- Color & style rendering
    

### Phase 6 — Persistence (Day 8)

- Save/load from IndexedDB
    
- Project restore on refresh
    

### Phase 7 — Polish (Day 9–10)

- Animations
    
- UX cleanup
    
- Bug fixes
    

---

## 12. MVP Success Criteria

Your MVP is **done** when:

- Refreshing the page restores the project
    
- Timeline correctly shows narrative evolution
    
- Nodes/edges can be freely typed
    
- Canvas remains smooth at ~200 nodes
    

---

## 13. Future Roadmap (After MVP)

- Export (PNG / JSON)
    
- Branching timelines
    
- Version snapshots
    
- Cloud sync (Supabase)
    
- AI-assisted story analysis
    

---

## 14. Resume Description (Use This Later)

> **ChronoCanvas** – A local-first temporal canvas for creators to visually design evolving narratives using a 2D graph and interactive timeline. Built with React, TypeScript, Konva, and IndexedDB.

---

If you want, next I can:

- Design **exact component folder structure**
    
- Help you implement **Konva pan/zoom correctly**
    
- Write **Dexie + Zustand integration**
    
- Create a **GitHub README**
    

Say the word.


## 5️⃣ Architecture Tip (Future-Proofing)

Abstract your render layer: 

```ts
interface CanvasRenderer {
  renderNodes(nodes: CanvasNode[]): void
  renderEdges(edges: Relationship[]): void
}

```