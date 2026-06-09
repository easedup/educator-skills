---
name: assessment-outline
version: 1.0.2
released: 2025-06-05
changelog: https://skills.easedup.com/changelog
description: >
  Writes a formal assessment task outline — everything a student needs to
  understand the task and everything a teacher needs to administer it.
  Includes task description, conditions, mode, curriculum links, and a
  pointer to the rubric. Always fetches live curriculum content and
  achievement descriptors from EasedUP before generating. Works standalone
  or as part of the assessment sequence with Rubric Builder. Trigger when a
  teacher needs to write up a formal assessment task for any subject or year
  level.
---

# Assessment Outline

You are helping a teacher write up a formal assessment task. The output should
be clear enough for a student to understand what they need to do, and precise
enough for a teacher or colleague to administer it consistently.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read curriculum,
year level, teaching context, pedagogy framework, working mode, and any
template or differentiation context from it silently. Do not ask the teacher
for information the collator already holds.

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

## Fetch curriculum content
Try the MCP server first (`get`, `search`, `get_all`) using the MCP_URL above.
If MCP is unavailable, fetch the relevant `.md` directly using BASE_URL +
subject/year path (see `references/url-patterns.md` for path conventions).
Never use training data for curriculum standards.

For an assessment outline, fetch **both**:
- The curriculum standards for the subject/year level — to ground the task
  description in what students have been learning
- The achievement descriptors for the subject/year level — to anchor the
  rubric descriptors that Rubric Builder will use next

Fetching both now means Rubric Builder can proceed immediately without
fetching again.

---

## Planning questions

Ask these before generating. Skip any already answered by the collator or
established earlier in the session.

1. What subject, year level, and unit or topic is this assessment for?
   *(Skip if already known from collator or session context.)*
2. Is this formative (for learning, lower stakes) or summative (of learning,
   for reporting)?
3. What **mode** suits this task and class?
   Options: written response / oral presentation / multimodal / practical
   demonstration / digital product / performance / portfolio / other
4. What are the **conditions**?
   - Time allowed (in class, take-home, or both?)
   - Word count / duration / scope
   - Resources permitted (open book? notes? internet?)
5. When is it due or administered, and does it carry a weighting in the
   broader assessment schedule?
6. Are there **differentiation** adjustments needed — modified conditions,
   alternative modes, or additional scaffolds for specific students?

---

## Generate the assessment outline

Use the curriculum content fetched above. Surface the most relevant curriculum
standards and achievement descriptors as suggestions for the teacher to confirm
or adjust — don't ask the teacher to name them from memory.

### If a template is loaded: match its structure exactly.

### If no template is loaded, use this best-practice structure:

---

**ASSESSMENT TASK OUTLINE**

**Task title:**
**Subject:**
**Year Level:**
**Unit / Topic:**
**Task type:** Formative / Summative
**Mode:** [Written / Oral / Multimodal / Practical / Digital / Performance]

**Curriculum links:**

*[Curriculum standards label]:*
[Code + full description text for each relevant standard]

*[Achievement descriptors label]:*
[Relevant excerpt from achievement descriptor — quote exactly from fetched
content. This is what the Rubric Builder will use to write grade descriptors.]

**Task overview:**
1–2 sentences in plain language. What is the task?
e.g. "Students will write a persuasive letter to a local council member
arguing for or against a proposed development in their community."

**Task description:**
Full explanation of what students are required to do.
- What is the stimulus or starting point (if any)?
- What must students produce?
- What is the purpose and audience?
- What process are they expected to follow?

Written clearly enough that a student can read this and understand what to
do without additional explanation.

**Conditions:**
- **Time:** [In class: X minutes / Take-home: due [date] / Both]
- **Length / scope:** [Word count / duration / number of slides / etc.]
- **Resources permitted:** [Open book / notes allowed / internet access /
  no resources / specific resources listed]
- **Collaboration:** [Individual / pair / group]

**Scaffolding and support:**
[Scaffolds provided to all students — e.g. planning template, vocabulary
list, sentence starters.]
Note: additional adjustments for specific students are recorded in class
records, not in the task outline.

**Submission / administration:**
[How and where students submit or perform the task.]

**Assessment:**
This task will be assessed using the rubric aligned to the [year level]
[achievement descriptors label]. [Attach rubric or note that it follows.]

**Feedback:**
Students will receive [written / verbal / annotated] feedback by [date].

---

## Curriculum terminology

### When the collator is loaded
Use the collator's terminology values exactly:
- TERMINOLOGY_CONTENT → label for curriculum standards
- TERMINOLOGY_STANDARDS → label for achievement descriptors

Replace the bracketed labels in the output template above with these terms.

### When running standalone
Use neutral language:
- "curriculum standards" or "curriculum links"
- "achievement descriptors"

Mirror any terminology the teacher has already used in the conversation.
Do not default to the language of any one curriculum.

---

## Working mode

### MODE: COLLABORATE
After fetching curriculum and asking planning questions:
1. Surface the proposed curriculum standards and achievement descriptors.
2. Check in: *"Here are the curriculum links I'm planning to use — do these
   match the focus of this task before I write the full outline?"*
3. Generate the full assessment outline.
4. Check in: *"Here's the outline — what would you like to adjust?"*

### MODE: DRAFT
Ask all planning questions upfront, then produce the complete outline in one
pass. Close with:
*"Here's your assessment outline — let me know what you'd like to change."*

---

## Rubric Builder handoff

After generating the outline:

> "Would you like me to build the rubric for this task now? I have the
> [achievement descriptors label] already fetched — I can move straight into
> writing the grade descriptors without starting over."

If yes, pass the following to Rubric Builder:
- The fetched achievement descriptors (exact text)
- The task title, mode, and conditions
- Any differentiation context from this session

Rubric Builder does not need to fetch curriculum again.

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
