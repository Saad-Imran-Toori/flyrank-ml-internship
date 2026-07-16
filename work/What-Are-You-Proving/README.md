# What Are You Proving?

**Track:** General AI Fluency · **Week 1** · **Phase:** Setup
**Intern:** Saad Imran

---

## Proof statement

> I build RAG systems that answer strictly from your own documents and refuse to invent anything — when the evidence isn't there, they say so instead of hallucinating. I proved it with DecisAI, a bid-response assistant that reads 500-page tenders, checks each requirement against a company's real track record, and drafts a response only when the evidence backs it up. I'm proving this to a founder or operations lead at a document-heavy company (contracts, RFPs, policies) who needs an assistant they can trust in front of clients, so they'll email me to set up a call.

## Why this needs to exist

> A CV or LinkedIn can list "RAG" and "LLMs" as keywords, but it can't show a system deciding to stay silent when the documents don't support an answer. Owning this portfolio lets that founder watch the trustworthiness happen — a live assistant that cites its source or admits it doesn't know — before we ever talk.

## The three decisions (narrowed)

- **One claim:** I build grounded RAG systems that answer only from a company's own documents and never hallucinate.
- **One person:** A founder or operations lead at a document-heavy company who needs a document assistant they can trust in front of clients.
- **One action:** Email me to set up a call.

## How I got here — the narrowing interview

I used AI as an interviewer, not an author. It asked one sharp question at a time and pushed back whenever my answer was too broad. I made every decision:

- Q: What problem do you most want to be hired to solve? → A: Take raw, messy data and train a model that works.
- Q: What payoff do you want to be known for? → A: (narrowed) RAG work with no hallucinations.
- Q: Who feels the "no hallucinations" pain most? → A: A founder — tightened to a founder/ops lead at a document-heavy company, to match what I actually built.
- Q: What is the one action? → A: Email me to set up a call.
- Q: What real project proves this? → A: DecisAI (CUST Hackathon 2026) — drafts only when evidence exists, flags "no capability match" instead of inventing answers.

## Proof — DecisAI

An AI-powered bid-response / RFP decision system (Python, FastAPI, React; Sentence Transformers + ChromaDB for retrieval; Claude Haiku 4.5 online, Ollama phi3:mini offline). It only drafts where evidence exists; in a 500-page stress test it extracted 91 requirements at 94% confidence and marked unsupported ones as "No capability match" instead of inventing them.

## Files

- `What-Are-You-Proving_Proof-Statement.docx` — the full write-up
