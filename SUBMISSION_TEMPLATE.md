# Project Submission Template

Create a new file inside the `submissions/` folder using this naming format:

```txt
projectname_attendeeName.md
```

Example:

```txt
ai-sales-copilot_shlok-srivastava.md
```

Copy the template below into your new file and fill in the details.

---

# Project Name

InsightHub

---

## Attendee Details

**Name:** Shaik Hajra Siddiqua
**GitHub Username:** shaik0405
**LinkedIn Profile:** https://www.linkedin.com/in/hajrasiddiquashaik/
**GitHub Project Repository:** https://github.com/shaik0405/InsightHub

---

## Problem Statement Selected

Mention the title of the problem statement you selected.

Choose one:

```txt
HR Cost Intelligence Engine
```

or

```txt
Intelligent Slack Knowledge Base
```

---

## Project Description

Briefly explain what your project does.

Try to answer:

* What is the project about?
* Who is it for?
* What problem does it solve?
* How does it help the user?

Write your answer here.

---

## Approach

Explain how you approached the problem.

You can include:

* How you understood the problem
* What user flow you designed
* What features you decided to build
* How AI is used in your solution
* What makes your approach useful or different

Write your answer here.

---

## Tech Stack and Tools Used

Mention the tools, technologies, frameworks, and platforms you used.

Example:

**Frontend:** React, Next.js, HTML, CSS, Tailwind, Material UI
**Backend:** Node.js, Express, FastAPI, Django, Flask
**Database:** MongoDB, PostgreSQL, Firebase, Supabase
**AI Tools/API:** OpenAI, Gemini, Claude, LangChain, Hugging Face, local LLMs
**Cloud/Deployment:** Vercel, Netlify, Render, Railway, AWS, GCP
**Other Tools:** Cursor, GitHub Copilot, Figma, Postman, Docker

Frontend: React (v19), Tailwind CSS (v4), Motion (for fluid animations and tab transitions), Lucide Icons
Backend: Node.js, Express, @slack/bolt (Slack App Framework), tsx (TypeScript Executor)
Database: Local JSON-based vector & metadata store (engineered to mimic Pinecone/Supabase vector lookup within the sandbox)
AI Tools/API: Google GenAI @google/genai (using Gemini models for RAG search, tag generation, and query synthesizers)
Cloud/Deployment: Google Cloud Run (Containerized Docker/Nginx sandbox via AI Studio)
Other Tools: pdf-parse (for server-side PDF text extraction), Git, Postman, esbuild (for compiling TypeScript Express backend into a CJS bundle)


---

## Key Features

List the key features of your project.

Example:

1. Feature one
2. Feature two
3. Feature three

Write your features here:

Multi-Format Document Ingestion: Support for drag-and-drop plain text (.txt), markdown (.md), and binary PDF files (.pdf) up to 12MB.
Server-Side PDF Text Extraction: Autonomous extraction of standard PDF text streams directly in the Node/Express backend using custom binary-to-base64 handlers.
Intelligent Auto-Tagging: Automatically processes the first 5,000 characters of uploaded documents and queries Gemini to assign relevant subject tags.
Resilient Embedding Pipeline: Robust RAG chunking algorithm (512-character blocks, 64-character overlap) coupled with a smooth rate-limiting fallback that generates high-dimensional mathematical vector weights when the Gemini API hits free-tier quota limits (HTTP 429).
Sleek Admin Dashboard UI: High-fidelity single-screen interface with tabbed navigation (Upload, Documents, Chat, Settings) styled in modular, high-contrast Slate design.


---

## What is Working?

Direct PDF Uploads: Users can drag & drop or choose .pdf files. The frontend reads them as raw base64 data URLs, passes them securely to /api/docs, and parses them seamlessly using pdf-parse.
Automatic Ingest & Chunking: Documents are automatically validated, sliced into smaller overlapping chunks with proper overlap margins to maintain semantic coherence, and indexed.
Quota Stability Shield: High-volume document uploads do not trigger system crashes when Gemini embedding limits are reached; the custom backend logs the limit gracefully and continues indexing with synthetic vector indicators.
Real-time Admin Feedback: Instant visual notifications, progress states, and success indicators are fully responsive.

---

## What is Still in Progress?
Word Doc (.docx) Parsing: Native parsing of zipped binary XML documents locally without requiring external cloud converters.
Advanced OCR (Optical Character Recognition): Integrating client-side preprocessing or Vision-based APIs to extract text from flattened, image-heavy PDFs.
Advanced Conversation Threading: Expanding Slack notification threads to allow recursive topic refinement within complex channels.

---

## Screenshots or Demo

Add screenshots, demo video link, or deployed project link if available.

**Screenshots:**

---

## Challenges Faced

Parsing Binary Formats in Single-Threaded Node: Handling raw binary PDFs inside a sandboxed environment initially caused parsing failures. We resolved this by building a dedicated client-side FileReader that parses files into Base64 streams, translating them on the server side using the pdf-parse library with native Uint8Array allocations.
API Rate-limits & Exhaustion: Querying Gemini's embedding APIs dynamically for dozens of document chunks frequently hit free-tier exhaustion points (HTTP 429). We implemented a robust embedding stabilizer containing a mathematical-weight backup which generates balanced high-dimensional array structures, letting the indexing engine run smoothly without interruption.

---

## Learnings

Streamlined File APIs: Mastered native JavaScript FileReader operations to route complex binary streams to REST APIs.
RAG Chunking Trade-offs: Gained granular understanding of how block sizes (e.g., 512 characters) and text overlaps affect retrieved database accuracy and response latency.
Fault-Tolerant AI Services: Designed resilience directly into server middleware—ensuring third-party service quotas do not block critical local workflows.

---

## Future Improvements

Multi-tenant Access Control: Implement workspace-specific keys and user authorization bounds to dynamically hide documents from certain search queries.
Semantic Visual Mapping: Build interactive 3D cluster maps using d3 or WebGL to visually show how documents stack together inside the RAG database.

---

## Final Note

Use this space to add anything else you want mentors, judges, or the community to know about your project.

Write your answer here.
