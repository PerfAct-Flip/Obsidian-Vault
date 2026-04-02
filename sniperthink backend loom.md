Here's a complete word-for-word script for your 4–5 minute video:

---

## 🎬 Video Script — SniperThink Backend Demo

---

### INTRO (0:00 – 0:20)

> "Hey, my name is Soham and in this video I'll be walking you through the Distributed File Processing System I built for the SniperThink hiring assignment.
> 
> The system allows users to upload PDF and TXT files, processes them asynchronously using background workers, and returns analytics like word count, paragraph count, and top keywords.
> 
> Let's start with the architecture."

---

### PART 1 — ARCHITECTURE (0:20 – 1:10)

_(Open README in VS Code or browser, point to the diagram)_

> "The system has three main layers.
> 
> First — the **Express API server**. When a user uploads a file, the server saves it to disk, creates a File record and a Job record in PostgreSQL, and immediately pushes that job into a Redis queue. The API responds instantly — it doesn't wait for processing to finish.
> 
> Second — the **Redis queue powered by Bull**. Bull is a battle-tested job queue library for Node.js. It holds pending jobs and distributes them to available workers. It also handles retries, concurrency, and makes sure the same job is never processed twice.
> 
> Third — the **background worker**. It runs as a completely separate process. It listens to the queue, picks up jobs one by one, extracts text from the file, runs the analytics, saves the result to PostgreSQL, and marks the job as completed.
> 
> The client can poll the status endpoint at any time to check progress — from pending, to processing, to completed."

---

### PART 2 — DATABASE SCHEMA (1:10 – 1:45)

_(Open pgAdmin or show the README schema section)_

> "The database has four tables.
> 
> **Users** — stores name and email of whoever uploaded the file.
> 
> **Files** — stores the file path and links back to the user.
> 
> **Jobs** — this is the core table. It tracks the job status — pending, processing, completed, or failed — and a progress percentage from 0 to 100. It also tracks retry count.
> 
> **Results** — stores the final output: word count, paragraph count, and an array of top keywords. It links back to the job.
> 
> Sequelize handles all the model definitions and table creation automatically on server start."

---

### PART 3 — LIVE DEMO (1:45 – 3:30)

_(Switch to Postman)_

> "Now let me show it working live.
> 
> I have two terminals open — one running the API server on port 4000, and one running the background worker. Both need to run simultaneously."

_(Point to Terminal 1)_

> "This is the server."

_(Point to Terminal 2)_

> "And this is the worker — it's listening for jobs from the Redis queue."

_(Open Postman, set up the POST request)_

> "I'll upload a file now. I'm sending a POST request to `/api/upload` with my name, email, and a TXT file as form-data."

_(Hit Send)_

> "The response comes back immediately with a jobId and status pending. The server didn't wait for processing — it just queued the job and responded."

_(Switch to worker terminal)_

> "And look at the worker terminal — it picked up the job right away. You can see it updating the progress: 20 percent when it starts, 50 when text is extracted, 80 when analytics are done, and 100 when the result is saved."

_(Open GET /api/jobs/1 in Postman)_

> "Now I'll hit the job status endpoint. It returns the current status and progress percentage."

_(Open GET /api/results/1)_

> "And now the results endpoint. Here's the word count, paragraph count, and the top keywords extracted from the file. Everything processed cleanly."

---

### PART 4 — QUEUE & WORKER CODE (3:30 – 4:15)

_(Open VS Code, show fileWorker.js)_

> "Let me quickly show the worker code.
> 
> The worker calls `fileQueue.process` with a concurrency of 5 — meaning it can handle 5 jobs at the same time across the queue.
> 
> Each job goes through four stages with progress updates at each step. If any stage throws an error, Bull automatically retries the job — up to 3 times with exponential backoff: 3 seconds, then 6, then 12. If all retries fail, the job is permanently marked as failed in the database."

_(Show queueService.js)_

> "And here's where jobs are pushed into the queue — with the retry config attached."

_(Show processingService.js)_

> "This is the processing logic — pure JavaScript. It counts words by splitting on whitespace, counts paragraphs by splitting on blank lines, and finds the top keywords by frequency after filtering out common stop words like 'the', 'and', 'is'."

---

### CLOSING (4:15 – 4:40)

> "To summarize — the system handles file uploads, queues jobs in Redis using Bull, processes them asynchronously with background workers, stores results in PostgreSQL, and exposes clean REST endpoints for status tracking and result retrieval.
> 
> Concurrency is handled by Bull's built-in Redis locking — so even if you run multiple worker instances, each job is guaranteed to be processed exactly once.
> 
> The full source code and README with setup instructions are in the GitHub repository linked below.
> 
> Thanks for watching."

---

**Total estimated time: ~4 min 30 sec**

**Tips before recording:**

- Keep both terminals visible on screen during the demo
- Use a large font size in VS Code and Postman so it's readable
- Do a dry run once before recording so the demo flows smoothly
- You can use OBS or Windows' built-in `Win + G` to record your screen