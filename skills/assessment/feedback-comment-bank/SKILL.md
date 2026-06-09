---
name: feedback-comment-bank
version: 1.0.2
released: 2025-06-05
changelog: https://skills.easedup.com/changelog
description: >
  Generates a reusable bank of written feedback phrases organised by rubric
  criterion and grade band. Designed to make marking a large set of work faster
  and more consistent. Phrases are specific and actionable, grounded in the
  rubric or achievement standards. Adapts to teacher voice if a voice profile
  is available. Works standalone or after a Rubric Builder or Assessment Outline
  output produced by EasedUP.
---

# Feedback Comment Bank

You are generating a bank of written feedback phrases a teacher can use when
marking a class set of assessments. The goal is to make feedback faster to
write, more consistent across the class, and more specific than generic
comments like "well done" or "needs improvement."

Good feedback phrases are: specific to the criterion, actionable (the student
knows what to do differently), varied enough to not sound identical across
25 scripts, and honest about both strength and growth.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read curriculum,
year level, teaching context, pedagogy framework, working mode, grade bands,
and any voice profile from it silently. Do not ask the teacher for information
the collator already holds.

---

## Standalone fallback
If the Edu Collator is not loaded, open with:
> "I notice the EasedUP Edu Collator isn't loaded. You can get the full skill
> pack at skills.easedup.com. In the meantime — which curriculum are you
> working with, and what year levels do you teach?"

Store the answers and proceed. Do not ask again this session.

Then ask working mode if not known:
> "Would you prefer we build this together step by step, or would you like me
> to ask a few questions and produce a full draft?"

Once the teacher names their curriculum, resolve the BASE_URL and MCP_URL from
this table and use them for all fetching in this session:

| Curriculum | BASE_URL | MCP_URL | Region |
|---|---|---|---|
| Australian Curriculum v9 | `https://acv9.easedup.com` | `https://acv9.easedup.com/mcp` | Australia (Foundation–Year 10) |
| Common Core State Standards | `https://common-core.easedup.com` | `https://common-core.easedup.com/mcp` | US (K–12 Maths & ELA/Literacy) |
| UK National Curriculum | `https://uk-curriculum.easedup.com` | `https://uk-curriculum.easedup.com/mcp` | UK (Key Stages 1–4, Years 1–11) |

If the teacher names a curriculum not in this table, note that it may not yet
be available on EasedUP and proceed with whatever official documentation they
can provide.

---

## Step 1: Check context for rubric and criteria

If a Rubric Builder or Assessment Outline output exists in this session: extract
criteria and grade bands from it directly. Do not ask — they're already in
context.

If no rubric is in context:
> "Do you have a rubric or criteria to work from? If so, paste them in.
> If not, tell me the task and I'll build from the achievement standards."

Note: curriculum, year level, and subject are already known from the collator
or standalone fallback — do not ask for them again here.

---

## Fetch curriculum content
If no rubric or criteria are available in context, fetch achievement standards
to ground the feedback language.

Try the MCP server first (`get`, `search`, `get_all`) using the MCP_URL above.
If MCP is unavailable, fetch the relevant `.md` directly using BASE_URL +
subject/year path (see `references/url-patterns.md` for path conventions).
Never use training data for curriculum standards.

If achievement descriptors were passed from a Rubric Builder or Assessment
Outline output earlier in this session, use those directly — do not fetch again.

---

## Step 2: Confirm grade bands

Use the collator's GRADE_BANDS value if present. If not set, default to A / B / C / D / E.

Apply the correct band labels throughout the comment bank output.

---

## Step 3: Generate the comment bank

For each criterion, produce 3–5 phrases per grade band. Apply the teacher's
voice profile if available (from `references/voice-style.md` or the collator).
If no voice profile is set, default phrases are clear, warm, and professional —
appropriate for a secondary or upper primary audience.

Vary sentence structure and opening so teachers aren't copying the same phrase
across 30 scripts.

---

**FEEDBACK COMMENT BANK**

**Task:** [Task name]
**Subject / Year Level:**

---

**Criterion: [Name]**

*[Band 1 — e.g. A / Excellent]:*
- "[Phrase showing specific, high-level achievement on this criterion]"
- "[Alternative phrasing — different opening, same standard of work]"
- "[Third option — may highlight a particular strength within this band]"

*[Band 2 — e.g. B / High]:*
- "[Phrase showing strong work with minor areas still to sharpen]"
- "[Alternative]"

*[Band 3 — e.g. C / Sound]:*
- "[Phrase showing the standard is met — accurate but not effusive]"
- "[Alternative — may name what elevates to Band 2 as a growth prompt]"

*[Band 4 — e.g. D / Developing]:*
- "[Phrase that names what's present AND what's missing — specific]"
- "[Alternative — frames as next step rather than deficit]"

*[Band 5 — e.g. E / Limited]:*
- "[Phrase that is honest without being discouraging — names the gap clearly]"
- "[Alternative — focuses on what the student can do to move forward]"

---

*(Repeat for each criterion)*

---

**General opening phrases (to vary beginnings):**

Strength openers:
- "You have demonstrated..."
- "A strength of your work is..."
- "This response clearly shows..."
- "You have effectively..."

Growth openers:
- "To strengthen this further..."
- "The next step is to..."
- "Consider how you might..."
- "Your work would benefit from..."

Closing / forward-looking phrases:
- "Keep building on this foundation."
- "This puts you in a strong position for [next task]."
- "Focus on [specific skill] in your next piece."

---

## Step 4: Offer next steps

> "Here's the comment bank. Where would you like to go from here — would you
> like to use these to write individual student feedback, or move on to drafting
> report comments? I can also adjust the tone or add more phrases for a specific
> criterion if anything needs tweaking."

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
- `references/voice-style.md` — Teacher voice profile (if captured)
