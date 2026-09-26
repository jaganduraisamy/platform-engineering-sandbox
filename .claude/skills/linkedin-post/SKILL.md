---
name: linkedin-post
description: Turns a tool-exploration/research session in this repo (e.g. Thanos, VictoriaMetrics, Mimir, OpenCost, ArgoCD, Kyverno — any platform-engineering tool the user has been reading docs on, comparing, or building a lab for) into a human-sounding LinkedIn post or article. Trigger this whenever the user asks to "write a linkedin post", "create an article about this", "share this as a post", "turn this into content", or similar, after a research/build session about a tool — even if they don't say "linkedin" explicitly but ask to "share what we found" or "write this up for others". Do NOT trigger for internal docs, READMEs, or commit messages — those stay in the repo, not on LinkedIn.
---

# Tool LinkedIn post

Turn a tool-research session into a LinkedIn-ready post. The credibility of these posts comes from being grounded in real, sourced facts and the user's own hands-on work — never invented adopters, statistics, or "lessons learned" that didn't actually happen.

## Why this structure

A tool post that's just "X is great, here's what it does" reads as marketing copy and gets scrolled past. What makes a technical post land: a real problem stated first, named companies/numbers as proof the tool matters beyond hype, and a first-person account of something that actually broke and got fixed. That last part is the whole reason to bother writing from a homelab instead of just summarizing docs — nobody else can tell that story.

## Before writing anything

1. **Pull what's already known from this session and the repo.** Check the conversation for tool internals, problems, and component breakdowns already discussed. Then check `docs/*.md` (design notes, roadmap) and the relevant numbered lab folder's `README.md` for anything documented there — cardinality issues, deployment gotchas, real bugs hit and fixed, verified behavior. This repo's own notes are the primary source for sections 2, 5, and 6 below; don't re-derive from scratch what's already written down.
2. **Identify every tool being covered.** A single-tool post skips section 3's comparison; a multi-tool comparison needs it per tool.
3. **Ask the user which format**, if they haven't said: a single long-form post (LinkedIn article length, ~800-1200 words), a short feed post (~150 words, one hook + one proof point), or a multi-part series (e.g. problem → comparison → build story, as separate posts). Don't guess — the right length changes what gets cut.

## Sourcing rule — the part that must not be skipped

Anything in section 3 (adoption evidence: named companies, CNCF/foundation maturity level, case-study numbers) or section 4 (other tools' internal components, if not covered in this session) that isn't already established in this conversation **must be verified with WebSearch before it goes in the post**. If a search doesn't turn up a solid source for a claim, cut the claim rather than soften it into vague language ("many companies use this") — vague filler is exactly the marketing-copy tone this skill exists to avoid. Cite nothing that can't be traced to either this session's own findings or a search result.

## Post structure

Write in this order. Skip a section only if it genuinely doesn't apply (e.g. single-tool post has no comparison section) — don't force content into a section that has nothing real to say.

1. **Hook** — one or two lines, first person, on why this problem/tool actually matters. Not "In today's cloud-native landscape..." — something closer to how the user would actually say it out loud.
2. **The problem being solved** — pulled from the repo's own research notes on the base tool's limits (e.g. Prometheus's cardinality/retention/global-view problems), stated in plain terms with the technical reason, not just "it doesn't scale."
3. **Tool intro + adoption proof** (per tool, if comparing more than one) — two lines of what it is, then real evidence it's used: named companies, a concrete before/after number from a case study, or foundation graduation status. Every fact here needs a source per the sourcing rule above.
4. **Core components** — short, accurate breakdown of how each tool is actually built (e.g. Thanos's Sidecar/Store Gateway/Compactor/Querier vs another tool's write-path/read-path split). Point out the shared pattern across tools if there is one — that's usually more interesting than the tool-by-tool list itself.
5. **Operational health tips** — mix well-known operational wisdom (what to monitor, what breaks at scale) with anything the user actually hit in their own build, pulled from the repo's docs/README notes. Real incidents outrank generic advice; lead with those if they exist.
6. **What was actually built** — the proof section. Summarize the user's own lab folder: what's deployed, what broke and how it got root-caused and fixed, what got verified working. This must be grounded in the actual repo/session state — check current file contents or recent command output rather than trusting memory of what was said earlier, since labs evolve mid-session.
7. **Closing line + hashtags** — short sign-off, 5-8 relevant hashtags.

## Formatting constraint

Output must be plain text, ready to paste directly into LinkedIn's post or article composer. LinkedIn does not render markdown: no `**bold**`, no `#` headers, no markdown tables, no `-` bullet lists rendered as lists (LinkedIn shows the literal dash). Use blank lines between sections and plain sentences instead of formatting to create visual structure. Section headers, if used at all, should just be a short bolded-sounding phrase on its own line in plain text — not a markdown heading.

## Tone

First person, conversational, some personality and imperfection allowed. Avoid: heavy bullet-point lists, corporate buzzwords ("leverage", "seamless", "robust solution"), a bullet-per-component recitation that reads like copied documentation. A post that sounds like it could have been written by any vendor's marketing team has failed, regardless of how accurate the facts are.

## After drafting

Show the draft in the conversation first. Then offer to save it to `docs/linkedin-posts/<tool-or-topic-slug>.md` in the current repo — this is what lets the user close the session and pick up edits in a new chat later without losing the draft. If the user has tweaks in-flight when this skill is invoked partway through editing, save the current state before ending the turn rather than leaving it only in chat history.
