# Handoff: Teaching AI Who You Are — Talk Takeaway Page

> **Context:** Toyesh Chakravorty is giving a 15-minute talk at Mindstone Amsterdam on May 20, 2026, titled "Teaching AI Who You Are." This repo is the take-home artifact — a single HTML page accessible via QR code at the end of the talk.

---

## Where Everything Lives

| Thing | Location |
|---|---|
| Repo | https://github.com/ToyeshC/mindstone |
| Live page | https://toyeshc.github.io/mindstone/ |
| Local build | `~/Documents/Personal/Coding/mindstone-talk/` |
| LinkedIn | https://www.linkedin.com/in/toyesh-c/ |

**Stack:** Single `index.html` with `<style>` block inline. No framework. No build step. `diagram.png` in the same directory. Hosted on GitHub Pages from `main` branch root.

---

## The Talk — What It Covers

**Title:** Teaching AI Who You Are  
**Duration:** 15 minutes  
**Audience:** Mixed. ~80% non-technical (ChatGPT/Claude.ai web users), ~20% technical (Claude Code/agent users).

**Four beats:**
1. **The Problem (2 min):** AI isn't lying — it's predicting. Same question, different framing, wildly different output. Live demo: two browser tabs, same question, two framings.
2. **What I Built (5 min):** A system around the model. Four layers: Identity, Memory, Tools, Constraints. Show the CLAUDE.md, show the setup. The hard part wasn't the code — it was writing the identity file.
3. **What It Changes (5 min):** Chat interface keeps you vulnerable (you're the system). Building the four layers makes you a director. Friction moves from execution to direction.
4. **The Close (1-2 min):** One thing to do tonight: write the identity file. Four questions. Show QR code.

**The four-layer framework (spine of everything):**
```
YOU
├── Layer 1: Identity     ← your AI readme
├── Layer 2: Memory       ← ongoing context
├── Layer 3: Tools        ← what it can do
└── Layer 4: Constraints  ← what it won't do
THE MODEL
```

---

## The Page — Current State

### Design (DONE, do not touch without reason)

- **Register:** Brand (speaker artifact, not a product UI)
- **Color strategy:** Committed. Warm cream base `oklch(97% 0.008 85)` + ochre accent `oklch(65% 0.14 75)`
- **Typography:** Spectral (Google Fonts, serif) for headings + Figtree (humanist sans) for body. Strong weight contrast. Fluid `clamp()` scale.
- **Aesthetic:** Zine/print-inspired. Narrow column (680px max), hierarchical density (sparse top, denser content), no cards, no icons above headings, no glassmorphism.
- **Mobile-first:** Scanned on a phone in a dim venue. Cream background works in any light.
- **NOT:** consulenco.nl (navy/cream/rose). This is Toyesh the speaker, not the consultancy.

### UX (DONE)

- Page opens on non-technical track by default
- Single `selectTrack('technical')` / `selectTrack('nontechnical')` JS function toggles a `body.show-technical` class
- Each section has one switch button at the bottom (scrolls to top of page and switches track)
- No fork buttons at the top — just scroll and switch at the end
- Print-friendly: both tracks render, switch buttons hidden
- `prefers-reduced-motion` respected
- `focus-visible` on all interactive elements

### Content — Non-Technical Track (MOSTLY DONE, needs data work)

- Four layers intro (3 sentences)
- Identity file worksheet: Tier 1 (4 philosophical questions) + Tier 2 (4 operational fields)
- Generic example identity file
- Where to paste it (ChatGPT custom instructions / Claude.ai Projects — with exact paths)
- Three conditional session prompts: Planning / Execution / Review
- "Small things add up" paragraph

### Content — Technical Track (MOSTLY DONE, needs data work)

- CLAUDE.md template (7 sections with placeholders)
- Real example (genericized from Toyesh's actual CLAUDE.md — financial/product builder context)
- Memory system pattern (4 file types, frontmatter, MEMORY.md index)
- Three session ritual variants: Planning / Execution / Review (with /session-start framing)
- Plan mode as a working pattern (4-step workflow)
- Hooks and notifications example (macOS notification JSON in settings.json)

---

## What Still Needs Work

### The Data Part (MAIN TODO)

This is the primary remaining work. "Data part" was flagged at end of last session but not fully specified. Based on context, it likely means one or more of:

1. **Richer examples in both tracks.** The identity file example and CLAUDE.md example are somewhat sparse. More concrete, opinionated examples would help people actually fill them in rather than stare at placeholders.

2. **The memory system section is thin.** It names the four file types and frontmatter but doesn't show an actual example memory file. A short example of what a `feedback_*.md` or `project_*.md` looks like would make it actionable.

3. **Session prompt depth.** The three prompts are good but the context for when to use each could be sharper. Maybe a one-line "what makes this session type different" header above each.

4. **The plan mode section.** Currently a 4-step list. Could be stronger with a concrete before/after: "without plan mode, here's what happens vs. with plan mode, here's what happens."

5. **Potentially: a downloadable/copyable block for each major piece.** Right now the identity file template and session prompts are readable but not obviously copy-paste-ready. Could add a subtle "copy" affordance or at least a note.

**Ask Toyesh at start of next session:** "Which part of the data do you want to fix first — the examples, the memory section, the session prompts, or something else?"

---

## Key Decisions Made (so you don't re-debate them)

| Decision | What | Why |
|---|---|---|
| One page, not two | Single HTML with track switching via JS class | Simpler QR, one URL, one file to maintain |
| Switch button at bottom only | No fork buttons at top | Cleaner — open the page, read your track, switch at the end if needed |
| Zine aesthetic | Print-inspired, narrow column, Spectral serif | Anti-startup, anti-AI-slop, personal speaker artifact feel |
| Cream, not dark | Light background | Phone in dim venue — cream works, dark would need different color logic |
| Ochre accent, not navy/rose | Personal, not consulenco.nl brand | Talk is Toyesh the person, not the consultancy |
| LinkedIn only, no email capture | Footer link, no form | Toyesh confirmed he won't maintain a list |
| Three session types | Planning / Execution / Review | Different session types need different opening frames — one merged prompt does none well |
| Tier 1 + Tier 2 in identity file | Philosophical + operational | Four questions get people thinking; operational layer makes it actually usable |
| Genericized CLAUDE.md example | Not the full project file | Real file is project-specific (Dutch financial data, API endpoints). Kept the voice, removed the context. |

---

## File Structure

```
mindstone-talk/
├── index.html     ← everything: HTML, CSS (in <style>), JS (inline <script>)
├── diagram.png    ← four-layer architectural diagram (AI-generated, ink style on cream)
├── README.md      ← one-paragraph description + live URL
└── HANDOFF.md     ← this file
```

---

## Parallel Project: Consult&Co (separate repo, separate work)

Toyesh is also running a hackathon project at:
- **Local:** `~/Documents/Personal/Coding/consult-and-co/`
- **Branch:** `toyesh`

**What it is:** Financial readiness tool for Fietsatelier Morgenwind BV (Dutch bicycle workshop). Responsible AI demo — system refuses to call Claude if data is dirty.

**Stack:** FastAPI backend + Next.js 16 frontend + direct Anthropic SDK (claude-sonnet-4-6) + LangWatch tracing.

**Hackathon date:** May 2026. Emma was the co-developer; she handed off and Toyesh now owns everything.

**Key file for context:** `consult-and-co/CLAUDE.md` — exhaustive project context including Dutch column names, check IDs, API routes, OAuth setup, key invariants.

**This is a completely separate project.** Do not confuse it with the Mindstone talk page.

---

## How to Continue

1. Open Claude Code in `~/Documents/Personal/Coding/mindstone-talk/`
2. Read `HANDOFF.md` (this file) and `index.html` to get oriented
3. Ask Toyesh what he means by "data part" — the likely answer is richer examples and a more actionable memory system section
4. Edit `index.html` directly (single file, no build step)
5. Push: `cd ~/Documents/Personal/Coding/mindstone-talk && git add index.html && git commit -m "..." && git push`
6. GitHub Pages auto-deploys within ~1 minute of push
7. Hard refresh (`Cmd+Shift+R`) to see changes

---

## Tone and Style Rules for This Page

From the master talk doc — apply to any copy edits:

- Write like you speak. Direct, no fluff.
- Short sentences.
- No buzzwords.
- If it sounds like AI wrote it, rewrite it.
- No em dashes. Use commas, colons, semicolons, periods.
- Every word earns its place.
