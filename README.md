# Sahil Mehta

**AI / Full-Stack Engineer at Enidus · NYC — open to relocation**

I build production LLM systems: agentic copilots, RAG, and the eval harnesses that keep them
honest. B.S. Computer Science + B.S. Data Science, UW–Madison 2025. 

My bias is that an agent claim isn't real until there's a number behind it and a test that can
fail.

### Currently

An **agentic copilot for T-Mobile for Business** — in pilot with 15 reseller tenants
representing 25+ enterprise customers and 100+ daily portal users. Natural-language queries over
telecom account data plus multi-step account actions: device purchase, line suspension, plan
upgrades.

- 53 intents dispatching to 43 Pydantic-typed tool handlers
- Every write-capable transaction is staged in an inline panel for human confirmation before the
  backend executes it — agent orchestration without autonomous write access
- A parametrized pytest suite (52 hand-designed cases fanning out to 400+ distinct invocations)
  covering intent dispatch, planning, and execution — it caught the agent inventing device SKUs
  and malformed account numbers early
- The LLM is constrained to tool selection, never raw SQL: parameterized templates,
  session-scoped row-level security, 8-role RBAC, per-tenant vector isolation

Alongside it, a self-serve reports and dashboards platform I built end-to-end alone, which cut
analytics turnaround from days to minutes.

**Open to** AI Engineer roles on small AI-first teams shipping real production LLM systems.

---

## What I'm shipping publicly

Four repos, in order of how production-grade.

### [CloudGuard](https://github.com/sahilmehta17/cloudguard) — a reliability and safety harness for LLM cloud agents

The headline artifact is the harness, not the agent. It measures the three things agent demos
skip, against a real AWS environment (Moto), with every headline number written to a committed
JSON artifact.

- A bag-of-words tool router degrades tool selection to **0.83** once the tool surface contains
  near-duplicates; an embeddings router recovers it to **1.00** (Claude Sonnet and Haiku)
- Blast-radius guardrails: **1.00** precision and recall on live-state destructive decisions
- An indirect prompt-injection red team that cut the hijack-attempt rate to **0%**
- Python · FastAPI · MCP · sentence-transformers · 57 tests

### [GoodEnough](https://github.com/sahilmehta17/GoodEnough) — where is a 1.7B model on a laptop CPU good enough to replace a hosted 70B?

Everyone knows you should route easy requests to a cheap model. Almost nobody ships it, because
you can't easily prove the cheap path didn't quietly get worse. GoodEnough measures that boundary
directly rather than asserting it: per benchmark slice, it reports whether the local model is
non-inferior **within a margin fixed before any evaluation data was observed**, below that margin,
or inconclusive at the available sample size.

A reproducible case study of two pinned deployment configurations — stated so it can be wrong.

### [ClaudeJob](https://github.com/sahilmehta17/claudejob) — an agentic resume-tailoring pipeline

Ingests live job postings, tailors a structured-output JSON resume per role, and generates
pixel-matching PDFs. I use it to power my own applications, which is the only reason its
guardrails are as paranoid as they are.

- A validator suite mirroring LLM-content failure modes: 30+ banned AI-resume cliché patterns,
  source-fact validation against a pinned base to catch fabricated stats, and a jargon-lead
  heuristic
- Adjacency-skill injection is deterministic and curated — never LLM-fabricated
- Node.js · Anthropic SDK · SSE streaming · pdfkit · 47 unit tests

### [chef-drop-brief](https://github.com/sahilmehta17/chef-drop-brief) — a Claude Code Skill with a real eval loop

Drafts Braze-ready lifecycle campaigns behind 9 deterministic copy evals. Bad input goes in, the
eval suite catches it, the skill revises once, then either ships or escalates to a human.

---

## [sahilmehta.dev](https://sahilmehta.dev)

My portfolio is a RAG agent over my own work — ask it something instead of scrolling. Next.js 16,
React 19, Claude Sonnet streamed over SSE, cosine similarity in plain JavaScript over a ~450KB
embeddings file (no vector DB; at ~50 chunks the network hop costs more than it saves).

Every answer carries inline citations back to the source chunk with its similarity score. There's
a public **[`/evals`](https://sahilmehta.dev/evals)** page showing the grading run for every
question in the suite — including the ones it fails.

---

## Toolkit

**AI/LLM systems** — LLM APIs (Claude, OpenAI), tool calling, agent orchestration, RAG, vector
search (Qdrant), eval frameworks, structured outputs (Pydantic), streaming/SSE, MCP, PyTorch,
TensorFlow

**Languages** — Python, TypeScript/JavaScript, SQL, Java, C, Kotlin, Swift, R

**Frameworks** — FastAPI, Node.js, Express, React, Next.js, Angular, Flask, Django

**Infra** — PostgreSQL, Docker, AWS, REST, gRPC, JWT/OAuth, RBAC · SnowPro Associate & Core (2024)

---

## Reach me

[sahilmehta.dev](https://sahilmehta.dev) ·
[LinkedIn](https://www.linkedin.com/in/sahil-mehta-87357b1b9/) ·
[sahilmehta0204@gmail.com](mailto:sahilmehta0204@gmail.com)

Email is fastest. I read everything.
