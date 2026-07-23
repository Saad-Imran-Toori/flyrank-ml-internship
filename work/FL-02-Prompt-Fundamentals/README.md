# FL-02 — Prompting Fundamentals on Real Tasks

**Track:** General AI Fluency · **Week 2** · **Phase:** Foundations
**Intern:** Saad Imran

---

A prompt iteration log built on a **real FL-01 audit task** (task #9, "Messages and emails"): getting an AI to draft a formal email asking my internship supervisor, Mr. Mirza Ašćerić (Director of AI Development, FlyRank AI), to complete the External Evaluation Performa my university requires.

I first worked through the basics chapters of the **Anthropic Prompt Engineering Interactive Tutorial** (Ch 1–3, plus 5–7). FL-02's five named techniques map almost one-to-one onto those chapters, so this log is that tutorial applied to a real task. All runs were in a fresh chat with no project instructions. Primary model: **Claude Sonnet 5**; cross-model: **ChatGPT**.

## The ladder (6 runs, one technique each)

| Run | Technique | What it did to the OUTPUT |
|---|---|---|
| Baseline | none (lazy prompt) | Asked me 3 clarifying questions and wrote **no email**. |
| Version 1 | role assignment | Produced a full email — but invented **5 placeholders** it had no facts for. |
| Version 2 | context and motivation | Placeholders gone — but invented "a fairly short form" and dropped my strongest fact. |
| Version 3 | output structure | Ask surfaced in sentence 2, fabrication removed, length halved — but went cold. |
| Version 4 | step decomposition | Reasoned out a smarter ask (willingness only, no attachment yet); self-corrected a presumptuous line. |
| Version 5 | few-shot examples | Finally sounded like me ("Thanks a lot") — but copied my casual register too far ("Hi Mirza"). |

Each version in the document carries four notes: what changed in the prompt, **what improved in the output**, what still failed, and what I'd try next. Every failure named the next technique.

## Cross-model comparison (Claude vs ChatGPT)

Three specific differences, not "both were fine":

1. **Opposite baseline instincts.** Same lazy prompt: Claude asked 3 questions and wrote nothing; ChatGPT immediately wrote a full email, inventing the purpose.
2. **ChatGPT refused the reasoning step.** On the final prompt, Claude showed all four thinking steps; ChatGPT replied *"Sorry, I can't provide my private reasoning or internal thought process"* and gave only a summary.
3. **Voice.** With the same few-shot examples, Claude matched my samples ("Thanks a lot"); ChatGPT kept its own formal default ("Thank you very much for your time and support") and added a signature block nobody asked for.

Takeaway: Claude was better at sounding like *me*; ChatGPT's greeting ("Dear Mr. Ašćerić") was better suited to a director. The ideal send is Claude's warm body with ChatGPT's greeting.

## Biggest lesson

Few-shot examples transfer **whatever is in them, including the parts you didn't intend**. My best result and my one real mistake both came from the same samples — great voice, wrong formality, because both samples were casual. The final template bakes this in as a caveat: choose examples whose register matches the situation.

## Files

- `FL-02_Prompt-Iteration-Log.docx` — the full log: all six versions with prompts, outputs, and four notes each; the cross-model comparison with ChatGPT screenshots embedded; and a reusable prompt template.
