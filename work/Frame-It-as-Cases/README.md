# Frame It as Cases — Work That Speaks for Itself

**Track:** General AI Fluency · **Week 2** · **Phase:** Foundations
**Intern:** Saad Imran

---

## Voice card

> Professional, plain, specific — start with the real problem, no buzzwords.

Added to my Claude Project as a standing instruction. Words I never use: leveraged, cutting-edge, robust, enterprise-grade, empowers, seamless, passionate, results-driven, at scale, unlock. Short sentences. Name the actual behaviour instead of describing it vaguely. If a line could describe any project, it gets rewritten so it could only describe mine.

## Who this is written for

- **The person:** a founder or operations lead at a document-heavy company — contracts, RFPs, policies — who needs an assistant they can trust in front of clients.
- **The action:** email me to set up a call.

## What the sitemap calls for

| Sitemap piece | Framed as |
|---|---|
| Hero | the claim line + call to action |
| Proof | Case 1 (DecisAI) and Case 2 (FlyRank internship) |
| About (inside the hero) | the bio |
| Contact | the contact copy |

## Bio

> Companies that run on documents — contracts, RFPs, policies — need an assistant that won't invent an answer when the file doesn't contain one. I'm a software engineering student at CUST who builds retrieval systems that answer from your own documents and say so when the evidence isn't there.

## Case 1 — DecisAI (CUST Hackathon 2026)

**The problem.** Proposal teams get RFPs and tenders running to hundreds of pages. Someone has to read every line, pull out the requirements, and work out whether the company can actually deliver — usually against a deadline.

**What I did.** Built by a team of three; my part was the retrieval layer. A company uploads its own bid history and capability records, which I chunked and embedded with Sentence Transformers into ChromaDB, so each extracted requirement can be matched against what the company has actually done before. Claude Haiku online, Ollama phi3:mini offline. The decision that shaped it: draft a response only where evidence exists, and mark "No capability match" where it doesn't. Retrieval was the hard part — anything past ~1,500 pages was slow and sometimes unusable. It was a hackathon, so I got it reliable at working sizes rather than chasing scale.

**What came of it.** Ran a 500-page synthetic tender end to end: 91 requirements at 94% confidence, unsupported ones marked rather than hidden. We did not place, but finished with participation badges and certificates and good feedback from the judges.

**What I would do differently.** Spend real time on retrieval performance past 1,500 pages.

## Case 2 — Prioritising 16,726 pages for review (FlyRank AI internship, in progress)

**The problem.** ~16,726 pages worth checking, an editor can review about 50 a week — a 335-week backlog. The question isn't "is this page underperforming?" (thousands are) but "which page should someone open first?"

**What I did.** Chose the CTR opportunity lane. My first idea: score each page by how far its click rate falls below the typical rate for its position tier. Before building on that, I tested whether the assumption held — it didn't. The tier rule was only 5.6% better than predicting one flat number for every page, and its top 100 pages all received the exact same score (2,530 pages, 15%, have zero clicks and score their tier median by definition). So it could not order the part of the list that actually gets used. That changed the design: learn what click rate a page like this normally gets, and rank by the shortfall — an observed measurement rather than my own arithmetic.

**What came of it.** The write-up had to be redone, because I'd already explained why the tier rule was a reasonable baseline. I wanted the submission correct rather than tidy. Still in progress — the model comes later. What exists now is a framed task, a metric chosen before modelling (MAE on unseen clients, plus precision@K), and a baseline to beat: 0.185.

**What I would do differently.** Test the assumption before writing the explanation of it.

## Contact copy

> If your team is buried in documents and you need an assistant you can put in front of a client, email me and we'll set up a call.

## Before and after

A real edit, not a manufactured example. While setting my voice card I was shown two versions of the same line and picked the first — then had it pointed out that it used six of the words my voice card bans.

**Before — generic AI line**

> Leveraged cutting-edge RAG architecture to deliver a robust, enterprise-grade solution that empowers proposal teams to unlock efficiency at scale.

**After — my version**

> DecisAI reads long RFPs and tenders, checks each requirement against a company's past project record, and drafts a response only where the evidence supports it. Where there is no supporting evidence, it flags the gap rather than filling it.

**What changed.** The first uses *leveraged, cutting-edge, robust, enterprise-grade, empowers, at scale* — six banned words in one sentence, and it could describe any AI product built by anyone. The second names what the system actually does and ends on the behaviour no competitor claims. The wider lesson: the first felt more professional because I've read thousands of sentences like it. That familiarity is exactly why it says nothing.

## Files

- `Frame-It-as-Cases.docx` — the full deliverable
