## 🎬 Frontend Video Script — 4.5 Minutes

---

### INTRO (0:00 – 0:25)

> "Hey I'm Soham. 
> I'm going to walk you through the frontend and backend for the SNIPERTHINK full stack assignment. 
> 
> First lets start with frontend!
> I'll cover three things — architecture decisions, how the animations work, and state management.
> 
> Let me show the final result first."

_(Scroll slowly through the live app)_

> "Five strategy steps, each animating differently as you scroll. A sticky progress indicator on the left, scroll-driven background effects, 3D hover on the cards, and an interest form that hits the backend API. Now let's break down how it's built."

---

### PART 1 — ARCHITECTURE (0:25 – 1:30)

_(Open VS Code, show src/ folder)_

--- 
> For animations I used Framer Motion. It's the most production-ready animation library for React.
_(Point to folder structure)_

> "The src folder has four areas — components, data, hooks, and styles.
> 
> The most important architectural decision is the **data layer**. All five step contents live in a single file — `steps.ts` — as a typed TypeScript array. No content is hardcoded anywhere inside JSX."

_(Open steps.ts)_

> "Each step object has an id, number, title, subtitle, description, icon, accent color, tags, and a stat value. The components just receive this data as props and render it.
> 
> This means if you want to add a sixth step, change a description, or reorder steps — you only touch this one file. The components need zero changes. That's clean, scalable architecture."

_(Open components folder)_

> "The component tree has four components with clear responsibilities.
> 
> `StrategyFlow` is the section wrapper — owns scroll tracking and active step state. `StepCard` is one strategy step — handles its own animation, 3D hover, and button click. `ProgressIndicator` is the sidebar — visualizes scroll position and which step is active. `InterestModal` is the form — handles validation, API call, and all feedback states.
> 
> Each component does one job. Nothing is doing too much."

---

### PART 2 — ANIMATION LOGIC (1:30 – 3:00)

_(Open StepCard.tsx, point to stepVariants)_

> "Let me walk through the animations. The assignment requires each step to animate uniquely — so I defined a `stepVariants` array with five completely different entrance animations.
> 
> Step 1 slides in from the left with a slight rotation. Step 2 drops from the top with a scale effect. Step 3 slides in from the right with a skew. Step 4 zooms in from the center with a rotation. Step 5 rises up from below.
> 
> Each card picks its variant based on its index in the array — so it automatically cycles through all five unique animations as you scroll down."

_(Point to useInView)_

> "These animations are triggered by the `useInView` custom hook — it wraps the browser's native IntersectionObserver. When a card enters the viewport, `inView` flips to true, and Framer Motion transitions the card from its hidden state to visible using spring physics. Smooth and natural."

_(Switch to browser, hover over a card slowly)_

> "Now the hover interaction — this is the user-triggered animation. When you move your mouse over a card, it physically tilts in 3D toward your cursor.
> 
> This is built with Framer Motion's `useMotionValue` and `useTransform`. I track the mouse X and Y position relative to the card center, and map those values to rotateX and rotateY. The card responds in real time to your cursor movement.
> 
> On hover the icon also shakes with a keyframe animation — a small detail but it makes the card feel alive and responsive."

_(Open StrategyFlow.tsx, show useScroll)_

> "For the scroll-driven animation — Framer Motion's `useScroll` hook gives me a `scrollYProgress` motion value, which goes from 0 to 1 as you scroll through the entire section.
> 
> I feed this into `useTransform` to move the headline upward as you scroll — a parallax effect. It also fades out after the first 15 percent of scroll.
> 
> The background orb uses the same scroll value to drift down and to the right — making the background feel dynamic and alive as you move through the page.
> 
> Critically — motion values in Framer Motion update the DOM directly through CSS transforms, completely bypassing React's render cycle. That's why there's no scroll lag."

_(Open ProgressIndicator.tsx briefly)_

> "The sidebar progress bar also uses the same `scrollYProgress` value — it scales vertically from 0 to 1 as a direct visual map of your scroll position. The dots fill with each step's accent color as you pass them."

---

### PART 3 — STATE MANAGEMENT (3:00 – 4:00)

_(Open StrategyFlow.tsx)_

> "State management is intentionally minimal. I didn't reach for Redux or Zustand — the component tree is shallow enough that React's built-in useState handles everything cleanly.
> 
> `StrategyFlow` has exactly two state values.
> 
> First — `activeIndex`. A number from 0 to 4 tracking which card is most visible on screen. It's updated by an IntersectionObserver watching all five cards simultaneously — whichever has the highest intersection ratio wins. This drives the progress indicator dots filling up.
> 
> Second — `selectedStep`. Either null or a step object. When it's not null, the modal renders. When the user closes it, it goes back to null. That's the entire open and close logic for the modal — one state value."

_(Open InterestModal.tsx)_

> "Inside the modal, the entire UI is controlled by a single `status` value — a TypeScript union type of idle, loading, success, or error.
> 
> When you click submit — status goes to loading, the button shows a spinner. If the API call succeeds — status goes to success and the form is replaced by a confirmation screen using Framer Motion's AnimatePresence. If it fails — status goes to error and a message appears. One value, four states, clean UI logic.
> 
> The API call itself is just a plain async fetch with try/catch — no Axios, no React Query needed for a single endpoint."

_(Open useScroll.ts)_

> "The custom hooks in `useScroll.ts` keep the components clean. `useInView` returns a ref, an inView boolean, and a progress value. You attach the ref to any element and it handles all the IntersectionObserver setup and cleanup internally. Components don't need to know any of that complexity."

---

### CLOSING (4:00 – 4:30)

> "To summarize —
> 
> **Architecture** — data-driven with a single source of truth in steps.ts, clean four-component tree, TypeScript throughout.
> 
> **Animations** — five unique entrance variants, scroll-driven parallax via useScroll and useTransform, 3D card tilt on hover via motion values, all running outside React's render cycle for smooth performance.
> 
> **State** — two values at the top level, local state inside cards and modal, no external library needed, TypeScript union types for clean status handling.
> 
> Full source code is on GitHub. Thanks for watching."

---

**Total: ~4.5 minutes**