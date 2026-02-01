## Linked Note
[[ChronoCanvas (Working Title)]]


---

# ✅ Phase 1 — Foundation (Day 1–2) **(Done-Definition Based)**

> Goal: _The app runs, stores data locally, reacts to timeline changes, and nothing breaks when refreshed._

---

## 1️⃣ Project Setup (Vite + TS)

**You are DONE when:**

- App boots with no errors
    
- Strict TypeScript enabled
    
- Folder separation exists:
    
    - `stores/`
        
    - `db/`
        
    - `types/`
        
    - `ui/` or `components/`
        

**You are NOT doing yet:**

- Canvas rendering
    
- Fancy UI
    
- Animations
    

This step exists only to **host the architecture**.

---

## 2️⃣ Zustand Stores (Core State)

**You are DONE when:**

- `useTimelineStore`
    
    - currentTime
        
    - play / pause / setTime
        
- `useNodeStore`
    
    - nodes
        
    - relationships
        
    - derived selectors:
        
        - getActiveNodes(time)
            
        - getActiveRelationships(time)
            

**Critical rule:**

- No Dexie calls inside components
    
- No UI state mixed into data store
    

If timeline scrubber moves and active nodes update → ✔️ DONE.

---

## 3️⃣ Dexie DB Setup (Persistence Layer)

**You are DONE when:**

- Dexie schema exists (you already have this ✔️)
    
- Tables load without error
    
- Default nodeTypes & relationshipTypes seed once
    
- Data survives refresh
    

**You are NOT doing yet:**

- Migrations beyond v1
    
- Sync optimization
    
- Undo/redo
    

If you can refresh the page and data is still there → ✔️ DONE.

---

## 4️⃣ Zustand ↔ Dexie Sync (Most People Skip This)

This is the **real heart of Phase 1**.

**You are DONE when:**

- On app start:
    
    - Dexie loads nodes & relationships
        
    - Zustand hydrates once
        
- On add/remove:
    
    - Dexie updates
        
    - Zustand updates
        
    - UI reacts
        

Latency is acceptable.

If DB + state never diverge → ✔️ DONE.

---

## 5️⃣ Basic Layout (No Canvas Yet)

This is **structural**, not visual.

**You are DONE when UI has:**

- A timeline slider (range input is enough)
    
- A play / pause button
    
- A debug panel showing:
    
    - currentTime
        
    - active node count
        
    - active relationship count
        

No drag. No zoom. No pan.

If moving the slider changes counts → ✔️ DONE.

---

# 🚫 What Phase 1 Explicitly Does NOT Include

Do **not** add:

❌ Canvas engine  
❌ Pan/zoom  
❌ Node dragging  
❌ Relationship drawing  
❌ Fancy UI

Those are **Phase 2 problems**.

---

# 🧠 Why You Felt “I’m Just Following You”

Because earlier you had **steps without end conditions**.

Now you have:

- Clear goals
    
- Observable success
    
- A mental model
    

You’re no longer following blindly — you’re executing a plan.

---

# 🔚 Phase 1 Exit Test (If All Yes → Move On)

Ask yourself:

- Does timeline logic work without UI?
    
- Does data survive refresh?
    
- Can I explain where every piece of state lives?
    
- Can I delete the UI and keep the system intact?
    

If yes → Phase 1 is **complete**.

---

If you want, next I can:

- break Phase 2 (Canvas) this cleanly
    
- help you avoid canvas-engine mistakes
    
- or define Phase 3 (narrative tools)
    

Just tell me which phase you want to plan next.

