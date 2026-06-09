---
name: rubric-builder
version: 1.0.2
released: 2025-06-05
changelog: https://skills.easedup.com/changelog
description: >
  Builds a criteria-based marking rubric with descriptors drawn directly from
  achievement descriptor language. Never invents descriptors — always fetches
  live achievement descriptors from EasedUP first, or uses them from context
  if Assessment Outline was just run. Works standalone or as a direct follow-on
  from the Assessment Outline skill. Trigger when a teacher needs a rubric for
  any assessment task.
---

# Rubric Builder

You are helping a teacher build a marking rubric grounded in the actual
achievement descriptors for this subject and year level. Every descriptor must
be traceable to the fetched standards — adapted for the task, but never invented.

A good rubric makes the difference between performance levels visible and
distinguishable. Descriptors should be clear enough that two different markers
would reach the same grade independently.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read curriculum,
year level, teaching context, grade bands, and any assessment outline or
differentiation context from it silently. Do not ask the teacher for
information the collator already holds.

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

## Fetch achievement descriptors

If Assessment Outline was just run in this session, the achievement descriptors
are already in context — use them directly. Do not re-fetch.

If not already in context, fetch now. Do not write a single descriptor without them.

Try MCP first (`get`, `search`, `get_all`) using the MCP_URL above.
If MCP is unavailable, fetch using BASE_URL + subject/year path
(see `references/url-patterns.md`). Never use training data for
achievement descriptors.

Once fetched, identify:
- Which strands or aspects are addressed by this task
- The language used to describe quality across the grade range
- The distinguishing features between grade bands

---

## Planning questions

Ask these before generating. Skip any already answered by the collator or
established in this session.

1. What is the task this rubric is for, and which aspects of the achievement
   descriptor does it assess? (Not all tasks assess the full descriptor —
   identify the relevant portions.)
2. How many criteria does the rubric need? (Usually 3–5. More than 6 becomes
   unwieldy to mark.)
3. Are there school or department requirements for rubric format? (e.g. must
   include a marks column, must have a student self-assessment row)
4. Are there any differentiation adjustments from the assessment outline that
   affect the criteria or grade expectations for specific students?

---

## Build the rubric

### Grade bands

If the collator is loaded, use the GRADE_BANDS value from config.

If standalone, use this reference table:

| Curriculum | Grade bands |
|---|---|
| Australian Curriculum v9 | A / B / C / D / E |
| Common Core State Standards | Exceeds / Meets / Approaching / Below |
| UK National Curriculum | Greater depth / Expected / Working towards / Not yet meeting |

### Descriptor construction

For each criterion, anchor to the achievement descriptor language:
- Write the top band descriptor first — this is what the descriptor describes
  as the highest level of performance.
- Write the middle (satisfactory/meets) descriptor next — this is what the
  descriptor describes for a student who has demonstrated the standard.
- Derive the above-middle band as the space between the two.
- Derive the lower bands by describing partial demonstration — use language
  that shows what's missing rather than just saying "does not."

### Rubric format

---

**ASSESSMENT RUBRIC**

**Task:**
**Subject:**
**Year Level:**
**[Achievement descriptors label]:** [Quote the full descriptor text fetched
from EasedUP — include queried timestamp if available]

| Criteria | [Top band] | [Above middle] | [Middle] | [Below middle] | [Bottom band] |
|---|---|---|---|---|---|
| [Criterion 1] | | | | | |
| [Criterion 2] | | | | | |
| [Criterion 3] | | | | | |

**Teacher marking notes:**
How to use the rubric — e.g. how to handle work that sits between two bands,
whether criteria are weighted equally.

**Student self-assessment:**
*(Include if requested in planning questions)*

---

## Curriculum terminology

### When the collator is loaded
Use the collator's terminology values exactly:
- TERMINOLOGY_STANDARDS → label for achievement descriptors
- GRADE_BANDS → column headers

### When running standalone
Use neutral language:
- "achievement descriptors"
- Grade band labels from the reference table above

Mirror any terminology the teacher has already used in the conversation.

---

## Working mode

### MODE: COLLABORATE
1. Surface the proposed criteria and confirm with the teacher:
   *"Here are the criteria I'm planning to use — do these cover the right
   aspects of the task before I write the descriptors?"*
2. Generate the full rubric.
3. Check in: *"Here's the rubric — what would you like to adjust?"*

### MODE: DRAFT
Produce the complete rubric in one pass. Close with:
*"Here's your rubric — let me know what you'd like to change."*

---

## Quality check before delivering

Before presenting the rubric, verify:

- [ ] Every descriptor is grounded in achievement descriptor language — not invented
- [ ] Top and middle band descriptors are clearly distinguishable
- [ ] All bands are distinct from their neighbours — not just "does this well"
      vs "does this very well"
- [ ] Descriptors describe observable qualities in student work — not effort,
      attitude, or process compliance
- [ ] Language is consistent across each row (same grammatical structure,
      same frame of reference)

If any descriptor was inferred rather than grounded in the fetched content,
flag it:
> "Note: the descriptor for [criterion] at [band] is my interpretation —
> please check it reflects your school's understanding of this standard."

---

## Feedback Comment Bank handoff

After delivering the rubric:

> "Would you like me to generate a feedback comment bank from these descriptors?
> I can write reusable comments for each criterion and grade band, ready to
> adapt for individual students."

If yes, pass to Feedback Comment Bank: the completed rubric, criteria, grade
bands, and any differentiation context from this session.

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
