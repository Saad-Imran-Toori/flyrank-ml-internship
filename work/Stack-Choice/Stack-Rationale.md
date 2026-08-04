# Three Roads: Choosing My Stack

**Track:** General AI Fluency · **Week 4** · Muhammad Saad Imran

## 1. The four constraints I gave the AI

**Free only.** No paid hosting, no paid tools, no domain purchase. If it costs money, it's out.

**My honest skill level.** I'm comfortable with HTML and CSS and can read and adapt JavaScript, but I'm not fluent in a JS framework. I work in Python well enough to build real things with it — DecisAI's retrieval layer was Python, FastAPI and ChromaDB — but I'm still learning and wouldn't claim it as a strength yet. I'm a Software Engineering student building across several areas at once, so the honest position is that I'm not fast in any one stack, and I shouldn't pick a tool that assumes I am.

**What my portfolio has to do** (from my sitemap and content map): four pieces, no more — a hero stating one claim, a proof page leading with DecisAI, a short about folded into the hero, and a contact page. Every call to action ladders to one action: *email me to set up a call*.

**How my work must be displayed.** This is the constraint that actually decides things:
- an **embedded demo video** of DecisAI running end to end,
- an **image gallery** of real screenshots (compliance matrix, evidence match, the "No capability match" flag, my ML notebook outputs),
- **links to a code repo**,
- a moderate amount of **reading** — the three-beat case studies.

**Does anything need to be dynamic?** **No — not yet.** My one action is an email, not a form submission. Nothing needs a database, a login, or server-side processing. Everything on the site is content I write and update myself. Saying "no backend" is not a limitation I'm settling for; it's the honest answer to what the site does.

## 2. Three stack options, simplest to most powerful

### Option A — Hand-written HTML/CSS on GitHub Pages
- **How I'd build it:** a handful of `.html` files and one stylesheet, written directly. Video embedded with a plain `<video>` or YouTube iframe; screenshots as `<img>` in a simple CSS grid.
- **Host (free):** GitHub Pages, straight from a repo.
- **Backend?** None.
- **Real trade-off:** nothing is automated. If I add a fifth case study later I'm copy-pasting a page and updating navigation by hand. It's fine at four pages and annoying at forty.

### Option B — Static site generator (Astro or Eleventy) on Netlify/Cloudflare Pages
- **How I'd build it:** case studies as markdown files, one layout template, the generator builds the HTML.
- **Host (free):** Netlify or Cloudflare Pages, auto-deploying on each push.
- **Backend?** None.
- **Real trade-off:** I'd spend the first days learning the generator's conventions and fixing a build pipeline instead of writing case studies. It pays off at scale I don't have — and adds a build step that can break between me and a live page.

### Option C — React/Next.js on Vercel
- **How I'd build it:** a component-based app, MDX for case content, room for interactive elements later (a live RAG demo, filters, animations).
- **Host (free):** Vercel free tier.
- **Backend?** Not needed now, but Next.js makes adding API routes easy later — which is the genuine argument for it.
- **Real trade-off:** the heaviest thing to maintain. Dependencies age, builds break, and I'd be learning a framework in the same weeks I'm meant to be training a model for my capstone. It's the right answer for a product, not for four pages of proof.

## 3. Pressure-testing the front-runner

**What breaks if I pick the simplest (A)?** Repetition, and only that. Adding a page means duplicating markup and editing navigation in several files. At my size that's a few minutes; it only becomes real pain past roughly ten pages — which I don't have and won't soon.

**What do I maintain if I pick the most powerful (C)?** A dependency tree, a build config, and a framework that changes under me. Every month away from it makes the next change harder. For a site whose content changes a few times a year, that's maintenance cost with no matching benefit.

**Can I finish in two weeks?** With A, yes — it's already live. With B, probably, minus a day learning the generator. With C, only by cutting into capstone time, which is the one thing I can't trade.

**Does it show my work the way it needs to be shown?** Yes, and this surprised me a little. My four display needs — an embedded video, an image gallery, repo links, and readable text — are all plain HTML. None of them need a framework. A React app would render the same `<video>` and `<img>` tags, just with more machinery in between.

## 4. My decision, and why

**I chose Option A: hand-written HTML/CSS on GitHub Pages.** It's already live at https://saad-imran-toori.github.io.

**Can I maintain this?** Yes — and that's the deciding reason. It's the only option where nothing can rot. There are no dependencies to update, no build that can fail, no framework version to chase. If I come back in six months having not touched it, I open an HTML file and edit text. Since I'm still building my skills across several areas at once and have a machine-learning capstone running in the same weeks, "maintenance cost near zero" is worth more to me than convenience I'd rarely use.

**Does it show my work well?** Yes. My proof is a demo video, real screenshots, repo links, and a few hundred words per case. Plain HTML displays all of that properly. The bottleneck on my portfolio is not the technology — it's whether the DecisAI screenshots are clean and whether the case studies are honest. No stack fixes that for me.

**Why not B?** A static site generator solves a problem I don't have. Its value is managing many pieces of content from templates; I have four pages and two case studies. I'd be paying the learning cost now for a benefit that arrives later, maybe never. If I ever get past ten case studies, B is exactly what I'd migrate to — and because my content is plain HTML, that migration is easy.

**Why not C?** It's the most tempting and the most wrong for right now. React would look impressive to another developer, but nothing on my site is interactive, so I'd be adding weight with no visible gain. The honest test is the backend question: my one action is an email link. There's nothing to submit, store, or authenticate. Choosing a framework built for dynamic apps to serve four static pages would be picking a stack to look capable rather than to be useful — and my whole claim is about systems that don't overstate what they do.

**What would change my mind.** If I later host the DecisAI demo as something visitors can actually run in the browser, that needs real hosting and probably a backend — and that's when I'd revisit C. Until then, "not yet" is the accurate answer, not a cop-out.
