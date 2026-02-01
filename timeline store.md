## Linked Note
[[zustand stores]]



Good — this is exactly the **right order** to learn Zustand: one store, one responsibility, fully understood.

I’ll **give the code** _and_ **explain every part**, line by line, but **only for Timeline state** (current time + play/pause). Nothing extra.

---

# Timeline Store (Current Time + Play/Pause)

## The Code (Minimal & Correct)

```ts
import { create } from "zustand";

type TimelineStatus = "play" | "pause";

interface TimelineStore {
  currentTime: number;
  status: TimelineStatus;

  setTime: (time: number) => void;
  play: () => void;
  pause: () => void;
  toggle: () => void;
}

export const useTimelineStore = create<TimelineStore>((set) => ({
  currentTime: 0,
  status: "pause",

  setTime: (time) => set({ currentTime: time }),
  play: () => set({ status: "play" }),
  pause: () => set({ status: "pause" }),
  toggle: () =>
    set((state) => ({
      status: state.status === "play" ? "pause" : "play",
    })),
}));
```

---

# Explanation (Important — Read Slowly)

## 1️⃣ Why This Store Exists

This store answers **two questions globally**:

1. _Where are we in the timeline?_ → `currentTime`
    
2. _Is the timeline moving or stopped?_ → `status`
    

Every part of your app depends on these.

---

## 2️⃣ `currentTime`

```ts
currentTime: 0
```

- Single source of truth for time
    
- Canvas reads this to decide:
    
    - Which nodes exist
        
    - Which relationships exist
        
- Timeline slider writes to this
    
- Play loop increments this
    

**Rule:**

> Changing time never mutates nodes — only this value.

---

## 3️⃣ `status: "play" | "pause"`

```ts
status: "pause"
```

This controls **behavior**, not data.

- `"play"` → time auto-increments
    
- `"pause"` → time frozen
    

You separate **what time is** from **whether time moves**.

This separation is critical for clean logic.

---

## 4️⃣ Why Actions Are Explicit

### `setTime`

```ts
setTime: (time) => set({ currentTime: time })
```

Used by:

- Timeline scrubber
    
- Jump-to-event buttons
    

This is a **direct, deterministic update**.

---

### `play` / `pause`

```ts
play: () => set({ status: "play" })
pause: () => set({ status: "pause" })
```

Why not pass strings everywhere?

Because:

- Fewer bugs
    
- Clear intent
    
- Easier refactor later
    

---

### `toggle`

```ts
toggle: () =>
  set((state) => ({
    status: state.status === "play" ? "pause" : "play",
  }))
```

Used by:

- Spacebar
    
- Play/Pause button
    

Encapsulates logic in one place.

---

## 5️⃣ How Components Should Use This Store (Conceptually)

### Timeline Slider

- Reads `currentTime`
    
- Calls `setTime()`
    

### Play Button

- Reads `status`
    
- Calls `toggle()`
    

### Canvas

- Reads `currentTime`
    
- Filters visible nodes
    

### Animation Loop

- Reads `status`
    
- If `"play"` → increment time
    

No component owns time logic — **the store does**.

---

## 6️⃣ One Very Important Rule (Don’t Break This)

❌ Do NOT increment `currentTime` inside the store automatically  
✅ Increment time in a loop _outside_, based on `status`

Why?

- Prevents hidden side effects
    
- Easier to pause, scrub, or jump
    
- Enables deterministic replay
    

The store stores **state**, not timers.

---

## 7️⃣ Why This Store Is “Correct”

- Single responsibility
    
- Predictable updates
    
- No UI assumptions
    
- Easy to extend:
    
    - speed
        
    - looping
        
    - markers
        
    - keyframes
        

---

## 8️⃣ When You’re Ready for the Next Store

Next stores should be:

1. **Core project data** (nodes, relationships)
    
2. **Selection state**
    
3. **Editor UI state**
    

Each with the same discipline:

> State + actions, no UI logic.

---

If you want next, I can:

- Review your **core project data store**
    
- Explain **timeline play loop design**
    
- Help you add **undo/redo safely**
    
- Show how **multiple stores communicate**
    

Say what you want next.
