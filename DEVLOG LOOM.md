Here's a detailed step-by-step script with exact mouse movements and what to say at every moment.

---

## BEFORE YOU START RECORDING

**Set up your screen:**

- Open browser with `devlog.vercel.app` on the landing page
- Open VS Code with these 4 files in separate tabs:
    - `src/app/api/entries/route.ts`
    - `src/lib/validations.ts`
    - `src/components/entries/EntryForm.tsx`
    - `src/app/log/page.tsx`
- Close all other apps
- Turn on Do Not Disturb
- Set Loom to record full screen
- Have a glass of water nearby

---

## INTRO — 0:00 to 0:15

**Action:** Stay on landing page, don't click anything yet

**Say:**

> "Hey, I'm Soham. This is DevLog — a developer learning journal I built for the internship assignment. It's a fullstack app built with Next.js 15, Prisma ORM, Postgres, Zod validation, and React Query. In the next 4 minutes I'll walk you through every feature, show you a complete API route with its validation and frontend data fetching, and talk about one real technical challenge I hit during the build. Let's go."

---

## PART 1 — FEATURE DEMO — 0:15 to 1:45

### Landing Page — 0:15 to 0:25

**Action:** Slowly move cursor across the three section cards on the landing page

**Say:**

> "This is the landing page. These three cards are already showing live data — entries logged, projects tracked, resources saved — pulled from the dashboard API on page load. Let's start with the core feature."

---

### Learning Log Feed — 0:25 to 0:45

**Action:** Click **Learning Log** card or navbar → wait for page to load

**Say:**

> "This is the Learning Log — a chronological feed of entries, newest first."

**Action:** Slowly scroll down through the entry cards

**Say:**

> "Each card shows the title, the date, a clean body preview — markdown symbols are stripped so it reads naturally — and tag chips at the bottom."

**Action:** Hover over one card slowly so edit and delete buttons appear

**Say:**

> "Hovering a card reveals edit and delete actions. These use stopPropagation so clicking them doesn't accidentally navigate into the entry."

---

### Entry Detail — 0:45 to 1:00

**Action:** Click on any entry card to open detail page

**Say:**

> "Clicking opens the full detail view. The body renders as proper markdown — you can see headings, code blocks, and lists all formatted correctly using react-markdown with the Tailwind typography plugin."

**Action:** Scroll down slowly to show linked projects and resources sections

**Say:**

> "Below the body you can see linked projects and attached resources. These are relational — one entry can be connected to multiple projects. Clicking a project navigates directly to its detail page."

---

### Create New Entry — 1:00 to 1:20

**Action:** Click **New Entry** button — modal opens

**Say:**

> "Let me create a new entry. The form is inside a modal — built as a reusable component used across entries, projects, and resources."

**Action:** Type a title — "Learned about React Query cache invalidation"

**Say:**

> "Title field — validated by Zod, must be non-empty and under 100 characters."

**Action:** Leave date as today, click into body field and type two lines

**Say:**

> "Body supports markdown. Date defaults to today."

**Action:** Click the tags input, type "react" and press Enter, type "typescript" and press Enter

**Say:**

> "This is a custom TagInput component I built. Press Enter or comma to add a tag, backspace on empty input removes the last one. Tags are upserted in the database — created if they don't exist, reused if they do."

**Action:** Click **Create Entry** button

**Say:**

> "On submit — Zod validates the request body on the API side, if anything fails it returns a 400 with field-level errors. On success—"

**Action:** Point to toast notification appearing bottom right

**Say:**

> "— a toast notification confirms it. And watch the feed—"

**Action:** Point to new entry appearing at top of feed

**Say:**

> "— the new entry appears instantly at the top without a page refresh. That's React Query's cache invalidation working."

---

### Projects Page — 1:20 to 1:30

**Action:** Click **Projects** in navbar

**Say:**

> "Projects page. Cards in a responsive grid — one column on mobile, three on desktop. Each card has a status badge with a distinct colour per status."

**Action:** Click the filter pills — Idea, Building, Shipped

**Say:**

> "Status filter pills at the top — clicking filters the grid client-side. No extra API call, just filtering the already-fetched data."

**Action:** Click one project card to open detail

**Say:**

> "Project detail shows description, tech stack tags, and all linked log entries. Clicking an entry navigates back to that entry's detail page — everything is connected."

**Action:** Press back button

---

### Resources Page — 1:30 to 1:45

**Action:** Click **Resources** in navbar

**Say:**

> "Resources is a bookmarker. Filter by category across the top — Article, Video, Docs, Course."

**Action:** Click the star icon on one resource card

**Say:**

> "Clicking the star toggles favourite — that's a PATCH request sending just the isFavourite boolean. The card updates instantly."

**Action:** Click the read toggle on another card

**Say:**

> "Same for read/unread. The card fades slightly when marked as read to visually distinguish it."

**Action:** Click **Favourites** filter pill

**Say:**

> "Filtering by Favourites shows only starred resources. Category and read filters work together simultaneously."

---

### Dashboard — 1:45 to 1:55

**Action:** Click **Dashboard** in navbar

**Say:**

> "Dashboard aggregates everything. Total counts at the top, a day streak counter — consecutive days with at least one log entry — an 8-week activity bar chart built with Recharts, and a top tags section showing the most used tags across all entries with relative frequency bars."

---

## PART 2 — CODE WALKTHROUGH — 1:55 to 3:25

**Action:** Switch to VS Code

**Say:**

> "Let me show you one complete vertical slice of the codebase — the entries POST route, its Zod schema, and the React Query mutation that calls it."

---

### API Route — 1:55 to 2:25

**Action:** Open `src/app/api/entries/route.ts`, scroll to the POST function

**Say:**

> "Here's the POST handler in `app/api/entries/route.ts`. This is a Next.js 15 Route Handler — it replaces the old pages/api pattern."

**Action:** Highlight `const body = await request.json()`

**Say:**

> "First we parse the raw request body."

**Action:** Highlight `CreateEntrySchema.safeParse(body)`

**Say:**

> "Then we pass it through `safeParse` from our Zod schema. `safeParse` returns a result object instead of throwing — so we can handle errors gracefully."

**Action:** Highlight the `if (!validated.success)` block

**Say:**

> "If validation fails we return a 400 with `flatten().fieldErrors` — this gives the frontend an object with per-field error messages, not just a generic error string."

**Action:** Highlight the tag upsert section

**Say:**

> "If validation passes, we upsert tags — create them if they don't exist, do nothing if they do. This is how 'React' stays one row in the tags table even across hundreds of entries."

**Action:** Highlight the `db.entry.create` call

**Say:**

> "Then create the entry with all relations in one Prisma query. The response is formatted to flatten the junction tables — so instead of returning `tags: [{ tag: { name: 'react' } }]` we return `tags: [{ name: 'react' }]`. Cleaner shape for the frontend."

---

### Zod Schema — 2:25 to 2:45

**Action:** Switch to `src/lib/validations.ts`, scroll to `CreateEntrySchema`

**Say:**

> "Here's the schema. Every field has explicit rules."

**Action:** Point to each field one by one

**Say:**

> "Title — string, non-empty, max 100 chars, whitespace trimmed. Date — required string. Body — required string. Tags and projectIds — arrays of strings, empty by default."

**Action:** Highlight `export type CreateEntryInput = z.infer<typeof CreateEntrySchema>`

**Say:**

> "This bottom line is important. `z.infer` generates a TypeScript type directly from the schema. I define the shape once — Zod gives me both runtime validation and compile-time type safety from the same source. No duplication."

**Action:** Scroll up slightly to show the schema is imported in the API route

**Say:**

> "The same schema is used in two places — the API route for server-side validation, and the form for client-side validation. One source of truth."

---

### React Query — 2:45 to 3:20

**Action:** Switch to `src/components/entries/EntryForm.tsx`

**Say:**

> "On the frontend, here's the form component."

**Action:** Highlight `resolver: zodResolver(CreateEntrySchema)`

**Say:**

> "The same Zod schema is passed to react-hook-form via zodResolver. This means before the form even makes a network request, the exact same rules run in the browser. If title is empty, the error shows inline immediately without hitting the API."

**Action:** Scroll to the `createMutation` block

**Say:**

> "The mutation uses React Query's `useMutation`. `mutationFn` is just an axios POST call — simple."

**action:** Highlight the `onSuccess` block

**Say:**

> "On success, `invalidateQueries` with the entries key tells React Query that the cached entries list is stale. React Query automatically refetches in the background and updates the UI. No manual setState, no manual refetch calls, no page reload."

**Action:** Highlight `queryClient.invalidateQueries({ queryKey: ["dashboard"] })`

**Say:**

> "We also invalidate the dashboard cache — because creating an entry affects the total count, the streak, and the weekly activity chart. All of those update automatically."

**Action:** Switch to `src/app/log/page.tsx`, highlight `useQuery`

**Say:**

> "And here's the query on the log page. `queryKey: ['entries']` is the cache key that connects everything together. When the mutation invalidates this key, this query refetches and the feed re-renders with fresh data."

---

## PART 3 — TECHNICAL CHALLENGE — 3:20 to 3:50

**Action:** Stay in VS Code or switch back to browser — either is fine

**Say:**

> "The biggest technical challenge I hit was database deployment. I built the entire app with SQLite locally — zero config, works great, database is just a file. Everything worked perfectly."

**Say:**

> "Then I tried to deploy to Vercel. SQLite doesn't work on Vercel because Vercel's filesystem is ephemeral — it resets on every deployment. My database file would get wiped every time I pushed code."

**Say:**

> "The fix was switching to Neon Postgres. But because Prisma migrations are provider-specific, I couldn't just swap the connection string. The migration files had SQLite-specific SQL in them. I had to delete the entire migrations folder and regenerate from scratch for Postgres."

**Action:** Open `prisma/schema.prisma` quickly

**Say:**

> "The actual code change was literally one word — changing provider from sqlite to postgresql in schema.prisma. Because Prisma abstracts the database completely, zero application code changed. Same queries, same API routes, same Zod schemas, same everything. Just a different provider string and connection URL."

**Say:**

> "That taught me something real about why ORMs matter — not just for convenience, but for genuine database portability. That abstraction paid off in a real situation."

---

## OUTRO — 3:50 to 4:00

**Action:** Switch back to browser, show the live app one more time

**Say:**

> "That's DevLog. Full repo is on GitHub with a README covering local setup, tech decisions, and known limitations. Live app is linked in the README. Thanks for watching."

---

## TIMING SUMMARY

```
0:00 - 0:15  Intro                    15 sec
0:15 - 0:25  Landing page             10 sec
0:25 - 0:45  Log feed                 20 sec
0:45 - 1:00  Entry detail             15 sec
1:00 - 1:20  Create entry             20 sec
1:20 - 1:30  Projects page            10 sec
1:30 - 1:45  Resources page           15 sec
1:45 - 1:55  Dashboard                10 sec
1:55 - 2:25  API route walkthrough    30 sec
2:25 - 2:45  Zod schema               20 sec
2:45 - 3:20  React Query              35 sec
3:20 - 3:50  Technical challenge      30 sec
3:50 - 4:00  Outro                    10 sec
─────────────────────────────────────
Total                                 4:00
```

---

## FINAL TIPS

```
✅ Do one full practice run without recording first
✅ Speak slower than feels natural — nerves speed you up
✅ Move the mouse slowly when showing code
✅ If you stumble just pause and continue — don't restart
✅ Keep water nearby — talking for 4 min dries your throat
✅ Use Loom's trim feature to cut any dead air at start/end
✅ Record in the morning when your voice is clearest
✅ Zoom browser to 125% so code is readable in recording
✅ Turn off all notifications before starting
```

Good luck!