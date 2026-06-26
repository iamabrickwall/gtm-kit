# Skill: Blog Post Creator

**Duration:** 45–75 minutes per post
**Output:** `outputs/content/[YYYY-MM-DD]-[slug].md`

---

## Quick Start

```
Read skills/blog-post-creator/SKILL.md and write a post on [topic]
```

Claude will read your positioning, ICP, persona, and the sponsorship decision framework, build a brief, draft the post in Newsletter Radar's voice, run an editorial QA pass against the "what not to say" rules, and emit one artifact with everything from brief to publishable markdown — ready for a human review pass before it lands in `../newsletter-radar-site/content/blog/[slug].md`.

---

## Purpose

Turn a single buyer question or topic into one publishable blog post that sounds like Newsletter Radar — direct, concrete, evidence-led — and never drifts into the framings we've explicitly ruled out (lead-gen, ROI claims, free-tier, competitor contrast as headline). The output is a draft for human review, not auto-publish.

---

## When to Run This Skill

- Publishing a new pillar or supporting post on the marketing site
- Turning a recurring buyer question into evergreen content
- Building out a content cluster around the retention thesis
- Responding to a category-moment (e.g. a competitor announcement) with a positioning-anchored take

Do NOT use this skill for:
- Outbound email copy → use `signal-to-sequence`
- Account-specific research → use `account-research`
- Sales battlecards → those live in `context/competitor-radar.md`

---

## Inputs

- A topic or buyer question (one line is enough)
- `context/profile.md` — pricing, stage, scope
- `context/positioning.md` — voice, value pillars, **what not to say**
- `context/sponsorship-decision-framework.md` — the retention thesis, metrics, framing
- `context/icp-definition.md` — to pick the right audience tier and exclude anti-ICP framings
- `context/personas/` — to identify the primary reader (default: Head of Growth)

If a context file is stale or missing, flag it once and continue with the best inference. Don't block on perfect inputs.

---

## Steps

### Step 1: Build the Brief (10 min)

Write a one-page brief that nails scope *before* you start drafting. Fill in:

- **Title (working):** a buyer-question framing, not a feature framing. ("How to choose newsletters by retention" beats "Newsletter Radar's retention analytics.")
- **Primary audience:** which persona from `context/personas/` is reading this? What stage of their buying journey?
- **Search intent:** what query would surface this post? Are we writing the answer to a question someone is already typing?
- **Thesis (one sentence):** what's the single argument the post makes? If you can't say it in one sentence, the post isn't ready.
- **Claim boundaries:** what we *will* claim (retention, tenure, repeat rate, competitor footprints, coverage breadth) and what we *will not* claim (ROI, conversion attribution, complete coverage, free tier).
- **CTA:** the no-signup sample lookup or "request early access" — never a free-trial framing.
- **Cluster map:** the pillar this post supports + 3–5 sibling/supporting posts that should link to or from it. Even if those posts don't exist yet, name them.

---

### Step 2: Draft the Outline (10 min)

Concrete headings, not topic gestures. Each H2 should answer a specific buyer sub-question. Five-section spine that usually works:

1. **The buyer's actual problem** — what they're trying to decide, not what they "should" care about
2. **Why the obvious approach is wrong** — most buyers use the wrong signal (subscriber count, media kit); name it specifically
3. **The retention/tenure lens** — the alternative signal, why it's more honest, with one concrete metric example
4. **How to apply it** — a practical framework, checklist, or 3-step process the reader can use today
5. **Honest caveats** — what this approach doesn't tell you, where it falls short

Add a sixth section only if the post truly needs it.

---

### Step 3: Write the Draft (20–30 min)

Voice rules from `context/positioning.md`:
- Direct, concrete, evidence-led, lightly technical (terminal/CLI brand)
- Lead with retention proof and specific footprints
- Never sound like a prospecting/lead-gen tool
- You are speaking to a highly technical audience — lead with logic and data in your assessments, not narrative or intuition. If a claim can't be backed by a number, a named example, or a clear causal chain, leave it out.

Style guardrails:
- Short paragraphs (1–3 sentences). Long paragraphs are an AI tell.
- Specific numbers and named examples over abstract claims. "8 of 14 sponsors run 12+ months straight" beats "high retention."
- Active voice. Plain verbs (decide, run, sponsor, retain) over ornate ones (leverage, utilize, foster, enhance).
- One real metric or specific scenario per H2 minimum.

Product truths to weave in naturally — at least two should appear in the draft:
- We crawl 1,000+ newsletters across tech, AI, business, finance
- The product reads both directions: company → newsletters, newsletter → companies
- Retention is the signal we surface (median tenure, repeat rate, anchor advertisers)
- Pricing: paid only, $99/mo Pro, $299/mo Team, no free tier
- 14-day money-back guarantee (the way we de-risk, since there's no free trial)

---

### Step 4: Editorial QA (5 min)

Run the draft against this checklist. A "fail" on any item means the draft isn't shippable — fix and re-check, don't paper over.

**Positioning — what NOT to say:**
- [ ] No lead-gen / prospecting framing. The post says "which newsletters to sponsor," never "who to pitch."
- [ ] No ROI / conversion / attribution claims. We talk about *revealed preference* (advertisers keep coming back), not conversion rates.
- [ ] No "complete coverage" claim. Coverage is honestly described as finite.
- [ ] No free-tier or free-trial implication. Sample lookup ≠ free trial.
- [ ] No competitor-contrast as the headline argument. The narrative stands on its own; competitor mentions are illustrative only.

**Voice — AI tells to strip:**
- [ ] No "delve," "crucial," "pivotal," "landscape," "foster," "enhance," "leverage," "utilize," "robust," "vibrant," "seamless," "groundbreaking"
- [ ] No "It is important to note," "Overall," "In conclusion," "Furthermore"
- [ ] No vague participles in headers: "highlighting," "underscoring," "reflecting"
- [ ] No vague authorities: "experts argue," "industry reports say," "studies show" without a named source

**Substance:**
- [ ] Every H2 has at least one specific number, named example, or concrete scenario
- [ ] The thesis from the brief actually appears in the draft (Step 1 sentence is somewhere in the body)
- [ ] CTA matches the brief and is not a free-trial offer
- [ ] At least two product truths from Step 3 appear naturally in the text
- [ ] Every assessment leads with logic or data (number, named example, causal chain) — never narrative or intuition. Audience is highly technical.

Record the QA result in the artifact (per the Output Format below) — list any items that needed a rewrite and what changed.

---

### Step 5: Save the Output (2 min)

Write the full artifact to `outputs/content/[YYYY-MM-DD]-[slug].md` using the structure below. The artifact contains *everything* — brief, cluster map, outline, QA, and the publishable markdown — so a reviewer can audit the work.

**Handoff to the site:** after human review, copy *only* the "## Publishable Markdown" section's contents (the frontmatter + body, no enclosing header) into `../newsletter-radar-site/content/blog/[slug].md`. Set `published: true` only when the post is final.

---

## Output Format

```markdown
# Blog Post: [Title]
Date: [YYYY-MM-DD]
Topic: [Topic]
Status: Draft ready for review

## Content Brief
- **Audience:** [Persona, stage]
- **Search intent:** [Query / question this answers]
- **Thesis (one sentence):** [The argument]
- **Claim boundaries:**
  - Will claim: [retention, tenure, repeat rate, footprints, coverage breadth — pick the relevant ones]
  - Will not claim: [ROI, conversion, complete coverage, free tier]
- **CTA:** [Sample lookup / Request early access]
- **Sources used:** [Files referenced]

## Cluster Map
- **Pillar:** [Pillar topic this post supports]
- **Siblings / supporting posts:**
  1. [Title — link target]
  2. [Title — link target]
  3. [Title — link target]
- **Internal links inserted in the draft:** [List]

## Outline
1. [H2 — buyer's actual problem]
2. [H2 — why the obvious approach is wrong]
3. [H2 — the retention/tenure lens]
4. [H2 — how to apply it]
5. [H2 — honest caveats]

## Editorial QA
Positioning:
- [x] No lead-gen framing
- [x] No ROI / conversion claims
- [x] No complete-coverage claim
- [x] No free-tier implication
- [x] No competitor-contrast headline

Voice:
- [x] No AI-tell vocabulary (list any that needed removal: ...)
- [x] No filler transitions
- [x] No vague participles in headers
- [x] No vague authorities

Substance:
- [x] Every H2 has a specific number / named example
- [x] Thesis appears in body
- [x] CTA matches brief
- [x] ≥2 product truths included

**Changes made during QA:** [Bullet list of edits, or "none"]

## Publishable Markdown

---
title: "[Title]"
description: "[1–2 sentence meta description, used on /blog index]"
date: "[YYYY-MM-DD]"
published: false
---

[The post body in markdown. Headings start at H2 since the page renders the H1
from the frontmatter `title` field. Short paragraphs. Specific numbers.
Internal links to the sibling cluster posts where they fit naturally.]
```

---

## Quality Check

Before saving the artifact, confirm:

- [ ] The brief's thesis is a *single sentence* that names a buyer decision
- [ ] The outline has ≥5 H2s, each tied to a buyer sub-question (not a feature)
- [ ] The Editorial QA section lists every checkbox, with edits noted where any failed
- [ ] The Publishable Markdown frontmatter has all four fields: `title`, `description`, `date`, `published`
- [ ] `published: false` until a human reviews and flips it to `true`
- [ ] The artifact filename matches the slug used in the frontmatter title (or close enough that a reviewer won't get confused)
- [ ] No paragraph is longer than 4 sentences in the publishable body
