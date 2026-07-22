# The Prompt Ladder

**Track:** General AI Fluency · **Week 2** · **Phase:** Foundations
**Intern:** Saad Imran

---

One prompt, improved across five versions — **one layer at a time**, output compared at every step. The task each run: *understand my FlyRank ML internship repo and tell me what to work on next.* Every run was in a fresh, project-free chat so nothing was helping the model behind the scenes.

**Headline finding:** my weak baseline was less embarrassing than expected, because my repo has a strong README the model could read. But **version 1 then made things worse, not better** — a clearer goal turned a vague-but-safe answer into a confident and *wrong* one. That failure is the most useful rung in the ladder.

## The ladder at a glance

| Run | Layer added | What it did to the OUTPUT |
|---|---|---|
| Baseline | none (lazy prompt) | Accurate tour of the starter template; nothing to act on. |
| Version 1 | a clearer goal | Turned description into a decision — but became **confidently wrong** (marked ML-03, already done, as "next"). |
| Version 2 | verification requirement | Became honest about what it had/hadn't checked — but **still reported the wrong status** (stale cached file it couldn't detect). |
| Version 3 | real context | Reconciled the conflict between my word and its fetch; reached the **correct** status and next step. |
| Version 4 | specified output format | Led with the answer; demoted the dispute out of the way. Clean, smooth win. |
| Version 5 | constraints | Sequenced by what **blocks** me — "request the gated dataset today, draft against the local CSV meanwhile." Correct → genuinely useful. |

## What each layer earned

- **Clearer goal** — turned a description into a decision, but also turned a safe-vague answer into a confident-wrong one.
- **Verification** — bought honesty about what the model had and hadn't checked, but couldn't fix an error hidden in stale data.
- **Real context** — let the model reconcile a conflict between my word and its evidence, and reach the right status.
- **Output format** — made the answer scannable and pushed the dispute out of the way.
- **Constraints** — turned correct advice into useful advice by surfacing the one blocker with a waiting period.

**Biggest lesson:** a "better" prompt is not always a better answer. Version 1 was more specific than the baseline and produced a worse, more dangerous result. Verification is what made the difference — not because it fixed the answer, but because it made the model honest about the limits of what it could see.

## Final reusable prompt

Cleaned up so another intern on this track could paste it in, fill the three bracketed parts with their own details, and get a status-and-next-step answer they can trust.

```
Here is my FlyRank ML internship GitHub repo: {your repo URL}

I want to know what I still have left to do and what to work on next.

Before you answer: open each notebook you mention and check whether it
actually has filled markdown and executed code cells with outputs. List
which files you opened and which you could not. If you cannot verify a
file, say so instead of guessing.

Context you can rely on: I have completed and committed {list the
assignments you have finished}. Everything else is still the untouched
skeleton. GitHub's raw file cache can lag, so trust this over a fetch
that disagrees.

My constraints: {your deadlines — e.g. lane locks end of Week 4, modelling
starts Week 5, paper ships Week 8; and any gated dataset access that needs
requesting ahead of time}.

Answer in exactly this structure, nothing before it:
1. STATUS — one line: X of N required assignments done.
2. NEXT — the single next assignment, and one sentence on why.
3. UNBLOCK NOW — anything to start today that has a waiting period or would
   block later work if left.
4. REMAINING — a short table: assignment code, notebook file, in order.
5. COULDN'T VERIFY — a short bullet list, or "nothing".
```

## Files

- `The-Prompt-Ladder.docx` — the full deliverable: all six runs with prompt, output excerpt, embedded screenshot, and four notes each.
