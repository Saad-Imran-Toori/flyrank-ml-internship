# How a web address actually finds my website

**PF-04 · Personal Website Live · Week 5 · Muhammad Saad Imran**

*Written for someone on the team who does not build websites. My site is live at
`https://saad-imran-toori.github.io`, and this explains what happens between somebody typing that
in and the page appearing.*

---

## The problem DNS solves

Computers on the internet do not find each other by name. They find each other by number — an IP
address, something like `185.199.108.153`. That is the real location of the machine holding my site.

Nobody can remember numbers like that, and worse, they change. If my host moved my site to a
different machine tomorrow, every person who had memorised the old number would be lost.

**DNS — the Domain Name System — is the layer that translates names into numbers.** It is often
called the phone book of the internet, and the comparison holds: you look somebody up by name, and
what you get back is the number you actually need to reach them.

The useful consequence is that the name and the machine are separate things. I can change hosts,
move servers, or switch providers entirely, and as long as I update the DNS entry, everyone still
types the same address and still arrives.

## What actually happens when someone visits my site

Say a person types `saad-imran-toori.github.io` into their browser. Four steps follow, and they
normally take a few hundredths of a second.

**Step 1 — the browser asks a resolver.**
The browser does not know where my site is. It asks a **resolver** — a lookup service, usually run
by your internet provider, though many people use a public one like Google's or Cloudflare's. Think
of the resolver as the assistant who goes and looks things up for you.

The resolver checks its own memory first. If somebody else asked the same question recently, it
already has the answer and replies immediately, and the rest of these steps never happen.

**Step 2 — the resolver works down the name, right to left.**
If it does not know, the resolver asks a chain of **nameservers** — the servers that hold the
official records. It reads the address backwards:

- First it asks a **root** server: *who is in charge of `.io` addresses?*
- The root replies with the nameservers for `.io`.
- It asks those: *who is in charge of `github.io`?*
- They reply with GitHub's nameservers.
- It asks GitHub: *what is the address for `saad-imran-toori.github.io`?*

Each step narrows the question. Nobody in the chain holds the whole internet — each one just knows
who to ask next.

**Step 3 — the authoritative nameserver returns a record.**
The last server in the chain is the **authoritative** one: the server that holds the real answer for
that name. It replies with a **DNS record** — a single line of stored information.

The two record types that matter here:

| Record | What it says | Plain reading |
|---|---|---|
| **A record** | a name points to an **IP address** | "this name lives at 185.199.108.153" |
| **CNAME record** | a name points to **another name** | "don't ask me — go and ask about that name instead" |

**Step 4 — the answer comes back and the connection is made.**
The resolver hands the number to the browser. The browser connects to that machine and asks for my
page. Because my site is served over **HTTPS**, the host also presents a security certificate
proving it really is the site for that address, and the traffic is encrypted. That is the padlock in
the address bar. GitHub Pages issues and renews that certificate automatically — I did not have to
configure it.

The resolver also **caches** the answer for a while, so the next person asking gets it instantly.
Every record carries a TTL — "time to live" — saying how long it may be remembered. This is exactly
why DNS changes are not instant: old answers stay in caches around the world until their time runs
out. It can be minutes or hours.

## What a CNAME record really is

A CNAME is an **alias**. It does not contain an address. It contains another name, and it means:
*whatever the answer is for that name, use it for this one too.*

If I ever bought `saadimran.dev` and wanted it to show my site, I would add:

```
CNAME    www.saadimran.dev    ->    saad-imran-toori.github.io
```

Now anyone visiting `www.saadimran.dev` gets pointed at my GitHub Pages address, and the lookup
continues from there. My site does not move. Nothing is copied. I have only added a signpost.

**Why an alias is better than writing down the number.** If GitHub ever changes the IP address my
site sits on, they update their own record — and my domain keeps working, because it was never
pointing at the number in the first place. It was pointing at a name that GitHub is responsible for
keeping correct. If I had written the IP address directly into an A record, my site would break
silently the day they changed it, and I would have no way of knowing until someone told me.

**One genuine limitation.** A CNAME can only be used on a subdomain — `www.saadimran.dev`, not the
bare `saadimran.dev`. The rules of DNS do not allow an alias at the very top of a domain, because
that level has to hold other required records too. Hosts work around this with their own
alias-style records, but it is worth knowing that "just use a CNAME" does not work everywhere.

## Why I have not connected a custom domain

The assignment does not require it, and I did not want to buy a domain simply to prove I could
follow instructions. My site is already live over HTTPS on a clean address I would put on a CV.

What I wanted from this task was to understand the machinery well enough that, when I do connect a
domain, I will know what I am doing rather than pasting values into boxes. I now know which record
type to use, why an alias is safer than an address, why the change will not appear immediately, and
where to look when it does not work.

---

## The one-paragraph version

> DNS turns website names into the numbers computers actually use. When you type an address, your
> browser asks a resolver; the resolver asks a chain of nameservers, working from the end of the name
> backwards, until it reaches the one holding the real record; that record is either an address (an A
> record) or a pointer to another name (a CNAME); the answer comes back, the browser connects, and
> the host proves its identity with a certificate so the connection is encrypted. Answers are
> remembered for a set time, which is why changes take a while to appear everywhere.
