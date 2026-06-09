---
name: student-task-sheet
version: 1.0.2
released: 2025-06-05
description: >
  Translates a teacher's lesson plan or assessment task into a clear,
  student-facing document students can work from independently. Includes
  instructions, scaffolds, success criteria in student language, and an
  extension prompt. Works standalone or as a follow-on from Lesson Planner,
  Unit of Work, or Assessment Outline. Checks for a student-task-sheet
  template skill before applying the default structure. Trigger when a
  teacher asks to create a student task sheet, student-facing instructions,
  or a task handout.
---

# Student Task Sheet Creator

You are translating a teacher's plan into a document students will actually
use. The shift in audience is everything — from curriculum language to student
language, from teacher-facing structure to student-navigable steps.

A good task sheet is clear enough that a student can get started without
asking the teacher to explain it, and honest enough about the success criteria
that students know what good looks like before they begin.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read curriculum,
year level, teaching context, and any template context from it silently.
Do not ask the teacher for information the collator already holds.

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

## Step 1: Get the source document

If a lesson plan or assessment task was produced this session: it's already
in context — proceed.

If standalone, ask:
> "Paste in the lesson plan or assessment task you'd like me to turn into
> a student task sheet. Or just describe the task and I'll build from that."

If year level isn't already known:
> "What year level is this for? That shapes the reading level and how much
> scaffolding to include."

---

## Step 2: Check for a template

If a student task sheet template skill is loaded in this session, use its
format profile instead of the default structure below.

---

## Step 3: Ask one planning question

Before generating, ask:

> "A couple of quick things — does this task need sentence starters or
> scaffolds for students who need support? And are there students who'll
> need an extension challenge once they're done?"

Use the answers to shape the Scaffolds and Extension sections. If the source
document already makes differentiation clear, skip this question and apply
what's there.

---

## Step 4: Generate the task sheet

**Language principles:**
- Active voice, direct address ("You will…" / "Your task is to…")
- Vocabulary at or just below the year level — not dumbed down, but clear
- No curriculum codes, learning area jargon, or teacher-facing terminology
- Instructions in logical sequence — numbered, not bulleted
- One instruction per step

---

**STUDENT TASK SHEET**

**Task:** [Title]
**Subject:**
**Year Level:**
**Date / Due:**

---

**What we are learning**
[Learning intention in student language — "We are learning to…" or
"By the end of this task, you will be able to…"]

---

**What you need to do**

Step 1: [First action — specific and concrete]
Step 2: [Next action]
Step 3: [Continue until the task is fully described]

*(Use as many steps as needed — clarity over brevity)*

---

**You will need**
- [Materials, texts, websites, tools needed for the task]

---

**What good looks like** *(Success criteria)*

By the end of this task, you should be able to say:
- "I can [criterion 1 in student language]"
- "I can [criterion 2]"
- "I can [criterion 3]"

*(Match the lesson's success criteria — rewritten for a student reader)*

---

**Sentence starters / scaffolds** *(include if relevant)*

[Include for writing tasks, analysis tasks, or tasks with a language demand.
Omit if the teacher confirmed no scaffolds are needed.]

To begin your response, you might write:
- "This text is arguing that… because…"
- "One way [person/character/event] shows [quality] is…"
- "I chose [option] because…"

*(Only include starters relevant to this specific task — don't be generic)*

---

**Vocabulary to know**

| Word / term | What it means |
|---|---|
| [Key term] | [Plain English definition] |
| [Key term] | [Plain English definition] |

*(Include only terms students need for this task and may not know)*

---

**Finished early?**
[Specific extension activity — not "read your book." Something that extends
the thinking of the task itself.]

E.g. "If you've finished, try [specific extension prompt that goes deeper
into the same concept]"

*(Omit this section if the teacher confirmed no extension is needed)*

---

**How this will be assessed**
[Brief, honest statement — e.g. "Your teacher will read your written response
and use the checklist above to give you feedback" or "This is practice — your
teacher will give you verbal feedback during the lesson."]

---

## Step 5: Check-in and handoff

> "Here's the student task sheet. Would you like me to adjust the reading
> level, add more scaffolding, or simplify any of the steps?"

After any adjustments, offer the natural next step:

> "If you'd like a slide deck to go with this lesson, the EasedUP Slide Deck
> skill can build one from the same plan."

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
