# FL-05 — Agent Concepts and MCP Basics

**Track:** General AI Fluency · **Week 4** · **Phase:** Build (core)
**Intern:** Muhammad Saad Imran

## Workflow vs agent — and what my FL-04 build is

A workflow follows a path someone already drew; an agent draws its own path as it goes.

**My FL-04 pipeline is a workflow.** I decide when to run it, I paste each prompt, the order never varies, and it has no tools — it only ever sees the notes I type into step 1. That is exactly why it kept flagging my figures as "unverified": it had no way to go and check.

## The three MCP primitives

- **Tools** — actions the model can invoke (read a file, run a command, call an API). They *do* something.
- **Resources** — data exposed for reading (a file, a record, a document). Context, not action.
- **Prompts** — reusable templates the server offers.

## My three MCP tasks (Claude Desktop as the MCP client)

| # | Task | Why chat alone could not do it |
|---|---|---|
| 1 | Read `D:\FlyRank AI _ Internship` on my machine | Returned my real archive: 4 week folders, 15 assignment folders, 60 files, and Week 4's exact contents. A chat model has no disk access and would have had to invent it. |
| 2 | Fetch `https://saad-imran-toori.github.io` live | Returned what the server is serving right now — title, meta description, body text. Only a real request can establish current state. |
| 3 | Run Python over the archive and write a new file | Counted files per week and wrote `mcp-task3-output.txt` to my Desktop — code execution plus a file that outlives the conversation. |

Evidence: screenshots of the three tool calls and their outputs.

## The one concrete agent upgrade

Give the **gather step** tools and a goal instead of a typed list: connect it to GitHub and my local archive, then ask it to *establish what I actually did this week*. It would query commit history, confirm notebooks have executed outputs, check the archive for deliverables, and decide for itself when it has enough — flipping the pipeline from asking me what happened to finding out.

The honest catch: an agent with repository access that misreads my history produces a wrong report **with citations**, which is more convincing and therefore more dangerous. Verification discipline would need to get stricter, not looser.

## Files

- `Agent-and-MCP-Explainer.md` — the 895-word explainer
- `mcp-task3-output.txt` — the file created live by MCP task 3
- MCP tool-call screenshots (attached to the submission)
