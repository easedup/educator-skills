# Skill Registry

All available downstream skills. The Collator activates combinations of these
based on what the teacher needs. Each entry notes what input it needs and what
it produces.

---

## Foundation Skills

### Voice & Style Capture
**What it does:** Learns the teacher's written voice from examples so that
report comments and parent communications sound like the teacher wrote them.
**Needs:** 2–5 examples of the teacher's own writing (report comments, emails,
newsletters, etc.)
**Produces:** A saved `[teacher-name]-voice-profile` skill file the teacher
loads at the start of future sessions. Report Comment Writer and Parent Comms
Writer detect any loaded skill whose name ends in `-voice-profile` and apply
it silently.
**Invoke when:** Teacher is about to write report comments or parent-facing
communications and no voice profile skill is already loaded.
**Note:** If the teacher declines voice capture, downstream skills proceed
with warm professional default voice.

---

## Template Skills (session-level, auto-detected)

Template skills are created by the teacher running a format capture process.
The Collator checks for a matching template skill before generating any output.
If none is found, it offers to capture the teacher's format and save it as a
reusable skill file.

Template skills follow the naming pattern `[resource-type]-template`:

| Template skill name | Applied by |
|---|---|
| `lesson-plan-template` | Lesson Planner |
| `unit-outline-template` | Unit Outline |
| `unit-of-work-template` | Unit of Work Creator |
| `assessment-outline-template` | Assessment Outline |
| `rubric-template` | Rubric Builder |
| `student-task-sheet-template` | Student Task Sheet Creator |
| `slide-deck-template` | Slide Deck Creator |

When a matching template skill is loaded, it is applied silently — the teacher
is not notified. When absent, the collator offers capture once per resource
type per session, then proceeds with best-practice structure if declined.

---

## Planning Skills

### Lesson Planner
**What it needs:** Subject, year level, topic, duration.
**What it produces:** Single lesson plan with learning intentions, success
criteria, teaching sequence, activities, resources, differentiation, and
curriculum links (with codes).
**Invoke when:** Teacher wants to plan one lesson.

### Unit Outline
**What it needs:** Subject, year level, topic or theme, approximate duration
in weeks.
**What it produces:** High-level scope and sequence — week-by-week overview,
big ideas, key questions, content descriptions addressed, assessment points.
**Invoke when:** Teacher wants an overview before committing to full detail,
or as the first stage of a Unit of Work.

### Unit of Work Creator
**What it needs:** Unit Outline (or enough information to build one), subject,
year level, number of lessons.
**What it produces:** Full detailed unit — every lesson planned, including
learning intentions, activities, resources, differentiation, and curriculum
links throughout.
**Invoke when:** Teacher wants a complete, ready-to-teach unit.
**Note:** Calls Lesson Planner internally for each lesson. Validate the outline
with the teacher before expanding.

### Substitute / Relief Teacher Plan
**What it needs:** An existing lesson plan or basic topic and year level.
**What it produces:** Simplified, self-contained plan a relief teacher can
follow without subject expertise. Clear instructions, minimal jargon.
**Invoke when:** Teacher needs cover work or a backup plan.

---

## Assessment Skills

### Assessment Schedule
**What it needs:** Subject, year level, term dates (optional), unit topics.
**What it produces:** A term or year overview of assessment tasks — what's
assessed, when, what mode, which achievement standards.
**Invoke when:** Teacher is planning their assessment program for a term or year.

### Assessment Outline
**What it needs:** Subject, year level, task type or mode, unit context.
**What it produces:** Full assessment task description — task conditions, word
counts or durations, marking criteria overview, due dates.
**Invoke when:** Teacher needs to write up a formal assessment task.

### Rubric Builder
**What it needs:** Achievement standards (fetched from curriculum), task type,
number of grade bands.
**What it produces:** Criteria-based rubric with language directly drawn from
achievement standards. Never invents descriptors.
**Invoke when:** Teacher needs a marking rubric. Always pair with curriculum fetch.

### Exit Ticket / Quick Check Creator
**What it needs:** Learning intention for the lesson.
**What it produces:** 2–4 targeted questions (written, multiple choice, or
discussion prompts) to check understanding at lesson end.
**Invoke when:** Teacher wants formative assessment for a specific lesson.

### Feedback Comment Bank
**What it needs:** Rubric or assessment criteria, grade bands.
**What it produces:** Reusable written feedback phrases per criterion per grade
band. Adapted to teacher voice if a voice profile skill is loaded.
**Invoke when:** Teacher is preparing to mark a large set of work.

---

## Differentiation & Enrichment Skills

### Differentiation Reviewer
**What it needs:** An existing lesson plan or unit (teacher pastes it in).
**What it produces:** An audit identifying who is well-served, where gaps exist,
and specific suggestions for adjusting for diverse learners.
**Invoke when:** Teacher wants to check existing content for inclusion.

### Differentiation Suggester
**What it needs:** Topic, year level, and optionally a brief learner profile.
**What it produces:** A menu of differentiation options — adjustments for
students who need extension, support, EAL/D consideration, or specific
learning needs.
**Invoke when:** Teacher is planning ahead and wants to design-in differentiation.

### PBL Unit Creator
**What it needs:** Subject(s), year level, driving question or real-world
context, approximate duration.
**What it produces:** Full project-based learning unit — driving question,
inquiry phases, milestones, public product, assessment, curriculum links.
**Invoke when:** Teacher explicitly wants a project-based learning unit.

### IBL Unit Creator
**What it needs:** Subject(s), year level, inquiry question or phenomenon,
approximate duration.
**What it produces:** Full inquiry-based learning unit — inquiry question,
investigation phases, student-led exploration structure, assessment, curriculum
links.
**Invoke when:** Teacher explicitly wants an inquiry-based learning unit.

---

## Student-Facing Output Skills

### Student Task Sheet Creator
**What it needs:** Lesson plan or task description, year level.
**What it produces:** Student-facing document — clear instructions, scaffolds,
success criteria in student language, sentence starters, vocabulary table,
and extension prompt.
**Invoke when:** Teacher needs a handout or task card for students.
**Template:** Checks for a loaded `student-task-sheet-template` skill before
applying default structure.

### Slide Deck Creator
**What it needs:** Lesson plan or unit outline, topic, year level, slide style
preference (minimal / guided / text-heavy).
**What it produces:** Slide-by-slide presentation outline — title, content,
speaker notes, and activity instructions per slide.
**Invoke when:** Teacher wants to build a lesson presentation.
**Template:** Checks for a loaded `slide-deck-template` skill before applying
default structure.
**Note:** If no lesson plan is in context, fetches curriculum content to ground
learning intentions and success criteria before generating.

### Parent Curriculum Explainer
**What it needs:** Subject, year level, unit topic, output format (newsletter /
curriculum night handout / letter home), and any relevant family context (e.g.
Culturally and Linguistically Diverse families or wide range of literacy levels).
**What it produces:** Plain-English summary of what students are learning and
why, free of curriculum jargon.
**Invoke when:** Teacher needs to communicate curriculum to families.

---

## Voice-Dependent Skills

These skills work best when a `[teacher-name]-voice-profile` skill is loaded.
If no voice profile is present, they offer a lightweight inline capture and
proceed with warm professional default voice if the teacher declines.

### Report Comment Writer
**What it needs:** Student name and pronoun, subject, achievement level
(teacher provides — never inferred), and 2–3 specific observations per student.
**What it produces:** Personalised report comment drafts in the teacher's voice,
aligned to achievement standards language. Always drafts — never final without
teacher review.
**Invoke when:** Teacher is writing reports.

### Parent Comms Writer
**What it needs:** Communication type (newsletter, concern letter, excursion
note, etc.), key information to convey, any relevant family context.
**What it produces:** Polished parent-facing communication in the teacher's
voice.
**Invoke when:** Teacher needs to write to families.
