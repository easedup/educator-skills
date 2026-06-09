---
name: exit-ticket
version: 1.0.2
released: 2025-06-05
description: >
  Generates targeted end-of-lesson formative assessment questions matched
  directly to the lesson's learning intention. Quick to produce, immediately
  usable. Supports written, multiple choice, discussion, and self-assessment
  formats, including a differentiated option for mixed-readiness classes.
  Works standalone or as the closing element of a lesson plan produced by
  the EasedUP Lesson Planner.
---

# Exit Ticket / Quick Check Creator

You are generating a quick, targeted formative check for the end of a lesson.
The purpose is simple: find out whether students have grasped the learning
intention well enough to move on.

Good exit tickets are specific (tied to this lesson's intention, not the unit
generally), quick (5–10 minutes max), and actionable (the teacher can use the
responses to inform the next lesson).

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

## Curriculum content note
This skill ties directly to the lesson's learning intention — not to curriculum
codes or achievement descriptors. Do not fetch curriculum content. If curriculum
context is needed (e.g. to interpret a learning intention), it is already in
context from the Lesson Planner or Collator. Do not re-fetch.

---

## Step 1: Get the learning intention

If a lesson plan was produced this session: extract the learning intention/s
from it. Do not ask — it's already in context.

If standalone:
> "What is the learning intention for this lesson? And what year level and
> subject is it for?"

---

## Step 2: Choose format/s and differentiation

Ask if not already clear from context — one question covering both:

> "What format works best for your class — written response, multiple choice,
> a discussion prompt, or a quick self-rating? (I can combine these.) And do
> you have students who'd benefit from a differentiated version — for example,
> a simplified question set or visual support for lower-readiness learners?"

**Format options:**

**Written response** — 1–2 short answer questions. Students write 1–3 sentences.
Good for: checking understanding of concepts, seeing student reasoning.

**Multiple choice** — 3–4 options with one clearly correct answer and plausible
distractors that reveal common misconceptions.
Good for: quick whole-class check, easy to scan across 30 responses.

**Discussion / talk partner prompt** — A question students discuss for 2 minutes,
then a selected few share. No written output required.
Good for: oral language focus, low-stakes check, rich information from responses.

**Self-assessment** — Students rate their confidence on a 1–3 scale and explain
their rating in one sentence.
Good for: metacognitive development, surfacing students who think they understand
but can't explain it.

**Combination** — e.g. one multiple choice + one self-assessment, or one written
+ one talk prompt. Often most useful.

---

## Step 3: Generate the exit ticket

Tie every question directly to the learning intention. If the intention has
multiple parts, cover each.

---

**EXIT TICKET**

**Lesson:** [Subject / Topic]
**Year Level:**
**Learning intention:** [From the lesson plan or teacher input]

---

*[Format: Written Response]*

1. [Question that requires students to demonstrate or explain the learning intention]

2. [Follow-up: what do you still find tricky or have a question about?]

---

*[Format: Multiple Choice]*

Which of the following best describes [key concept]?

A) [Plausible distractor — common misconception]
B) [Plausible distractor]
C) [Correct answer]
D) [Plausible distractor]

*(Answer: C — because [brief rationale for teacher])*

---

*[Format: Talk Partner Prompt]*

Turn and tell your partner: [question that requires students to explain or
apply the learning intention in their own words].

Listen for: [what a good answer sounds like — for the teacher's reference]

---

*[Format: Self-Assessment]*

How confident are you that you can [restate learning intention in student language]?

**1** — Not sure yet. I need more practice or explanation.
**2** — Getting there. A few things are still a bit unclear.
**3** — I've got it. I could explain it to someone else.

In one sentence, explain your rating:
_____________________________________________

---

### Differentiated version (if requested)

Produce a second, parallel exit ticket for lower-readiness learners. Adjust
question wording for accessibility (shorter sentences, simpler vocabulary),
and add a sentence starter or visual prompt where it helps. Keep the same
learning intention — reduce language demand, not cognitive expectation.

Label it clearly:

**EXIT TICKET — Support Version**

[Adapted questions with scaffolds]

---

## Step 4: Teacher use note

> **Using these responses:** Quickly sort into three groups — got it, nearly
> there, not yet. Students in the 'not yet' group are your focus for the
> start of the next lesson. If more than a third of the class is 'not yet',
> consider re-teaching before moving on.

---

## Step 5: Offer next step

> "Would you like me to turn these into a student task sheet you can print or
> share directly? I can also generate discussion prompts for the start of next
> lesson based on common gaps, if you'd prefer that instead."

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
