# Agents, MCP, and What My Pipeline Is Missing

**FL-05 · General AI Fluency · Week 4 · Muhammad Saad Imran**

## What an agent actually is

The clearest way I've found to think about it: **a workflow follows a path someone already drew; an agent draws its own path as it goes.**

In a workflow, the steps and their order are fixed before anything runs. The model does work at each step, but it never decides *which* step comes next — a human or a script decided that in advance. Anthropic's engineering essay makes the point that most systems marketed as "agents" are really workflows with good copywriting.

An agent differs in one specific way: it is given a goal and a set of tools, and it decides for itself which tool to reach for, in what order, and when the job is done. It runs a loop — act, observe, decide the next move — directed by the model rather than by me. The trade-off is real: workflows are predictable and easy to debug; agents are flexible and much harder to reason about when they go wrong.

**My FL-04 pipeline is a workflow, not an agent.** I built a four-step "draft, critique, revise" process for my weekly university report: gather tasks into a table, draft from that table, critique against a rubric, revise only what the critique flagged. It looks sophisticated because the steps hand off cleanly and the critique genuinely catches things — in one run it noticed I was trying to close a week that hadn't finished yet, and in another it spotted two assignments missing from my sequence.

None of that makes it an agent. **I** decide when to run it. **I** paste each prompt. The order never varies. It has no tools, so it only ever sees the notes I type into step 1. When it flagged my figures as "unverified," it was being honest about a hard limit: it had no way to go and check.

## What MCP is

The Model Context Protocol is an open standard for connecting a model to things outside the chat window. The docs call it a USB-C port for AI applications, and the analogy holds — before it, every integration was custom-built for one model and one service. MCP defines one shape any client and server can speak.

There are **three primitives**:

- **Tools** — actions the model can invoke (read a file, run a command, call an API). These *do* something and can change state.
- **Resources** — data the server exposes for reading: a file, a record, a document. Context, not action.
- **Prompts** — reusable templates the server offers, so common interactions aren't rewritten each time.

The split is a safety design as much as a technical one. Reading a resource and executing a tool carry different risk, so a client can ask permission for one without blanket-approving the other.

## My three MCP tasks

I ran these through Claude Desktop, an MCP client. All three produced tool calls; none could be done by plain chat.

**1 — Read files on my own computer.** It read `D:\FlyRank AI _ Internship`, a folder existing nowhere but my machine, and returned the real structure: four week folders, 15 numbered assignment folders, 60 files, and Week 4's exact contents. A chat model would have had to invent all of it.

**2 — Query a live service.** It fetched `https://saad-imran-toori.github.io` and reported what the server actually returned — my live page's title, description and body text. That's the current state of a website, not a memory, which only a real request can establish.

**3 — Execute code and write a file.** It ran a Python script that walked my archive, counted files per week, and wrote the result to a new file on my Desktop. Two capabilities at once: running code, and creating something that outlives the conversation.

The pattern is consistent. Plain chat produces text *about* the world; with MCP the model can read the world, query it, and change it.

## What my workflow needs to become an agent

The gap is in step 1. My pipeline's biggest weakness is that gathering depends entirely on the quality of my notes — garbage in, confidently formatted garbage out. Every run flagged the same thing: my figures were "quoted from your notes and unverified."

**The concrete upgrade: give the gather step tools, and let it decide what to check.**

Instead of receiving a list I typed, step 1 should get an MCP connection to GitHub and my local archive, plus a goal: *establish what I actually did this week*. It would query commit history for the date range, read the notebooks to confirm they have executed outputs, check the archive for deliverables, and cross-reference all of it — deciding for itself which sources to check and when it has enough. That flips the pipeline from asking me what happened to finding out. The critique step sharpens too, because it can check claims against evidence rather than against other claims.

It would also introduce a new problem. A workflow that misreads my notes produces a wrong report and I catch it. An agent with repository access that misreads my history produces a wrong report *with citations* — more convincing, therefore more dangerous. The verification discipline would need to get stricter, not looser: the same lesson my DecisAI project is built on, that a system able to act needs a clearer account of when it should refuse.
