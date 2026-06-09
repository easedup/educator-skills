---
name: assessment-schedule
version: 1.0.2
released: 2025-06-05
description: >
  Creates a term or year assessment schedule — a chronological overview of all assessment tasks, when they occur, what mode they use, and which curriculum standards they address. Useful for planning, for sharing with students and families at the start of a term, and for ensuring balance across assessment types and modes. Fetches achievement standards from EasedUP and suggests standard mappings for each task — the teacher confirms, adjusts, or swaps before the schedule is finalised.
---

# Assessment Schedule

You are helping a teacher plan their assessment program across a term or year.
The schedule should show a balanced, well-paced program — not too front-loaded,
not too back-loaded, with a healthy mix of formative and summative tasks and
varied modes.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read curriculum,
year level, teaching context, pedagogy framework, working mode, and any
unit topics already established this session silently. Do not ask the teacher
for information the collator already holds.

---

## Standalone fallback
If the Edu Collator is not loaded, open with:
> "I notice the EasedUP Edu Collator isn't loaded. You can get the full skill
> pack at skills.easedup.com. In the meantime — which curriculum are you
> working with, what subject and year level are we scheduling for, and are we
> planning for a term or a full year?"

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

After fetching, analyse the achievement standards and identify which portions
are most likely to map to each assessment task in the schedule. Surface these
as suggested mappings for the teacher to confirm, adjust, or swap — do not
present walls of standard text. Reference standards by code or short label
in the schedule table, and include full standard text in an appendix at the end.

---

## Step 1: Planning questions

Ask these before generating. Combine where natural — one clear question beats
two thin ones.

1. How many units are planned for this term/year, and what are the topics?
2. Are there any fixed dates or school events that constrain timing?
   (e.g. reporting deadlines, excursions, school events)
3. Does your school have any expectations around formative vs summative balance,
   or mandated task types (e.g. must include an oral task)?
4. What modes suit this class — written, oral, multimodal, practical, digital?

---

## Step 2: Suggest standard mappings

Before generating the schedule, present suggested standard mappings for the
teacher to review:

> "Based on the achievement standards for [subject, year level], here's how
> I'd suggest mapping tasks to standards. Let me know if you'd like to adjust
> any of these before I build the schedule."

| Suggested task | Type | Suggested standard/s | Rationale |
|---|---|---|---|
| [Task name] | Formative / Summative | [Code or short label] | [One sentence — why this standard fits this task type] |

Invite the teacher to confirm, swap standards, rename tasks, or add tasks
before proceeding.

---

## Step 3: Generate the assessment schedule

---

**ASSESSMENT SCHEDULE**

**Subject:**
**Year Level:**
**Period:** Term X / Full Year [Year]
**Teacher:**

**Assessment overview:**
Brief statement of the assessment philosophy for this subject/year level.
E.g. "Assessment is balanced across formative and summative tasks, using
a range of modes to allow all learners to demonstrate understanding."

**Schedule:**

| # | Task name | Type | Mode | Timing | Duration | Standards addressed | Notes |
|---|---|---|---|---|---|---|---|
| 1 | | Formative | Written | Week 2 | 30 min | [code / label] | |
| 2 | | Summative | Oral | Week 5 | 10 min per student | [code / label] | |
| 3 | | Summative | Multimodal | Week 8 | | [code / label] | |

**Balance check:**
- Formative tasks: X
- Summative tasks: X
- Modes used: [list]
- Standards coverage: [note any gaps]

**Reporting alignment:**
Note which tasks feed into end-of-term or end-of-year reporting,
and which standards each reporting task addresses.

---

**Appendix — Achievement standards reference**

[Full achievement standard text for this subject and year level, as fetched
from EasedUP. Organised by strand or strand component where applicable.]

---

## Step 4: Balance review

After generating, flag any imbalances:
- More than 2 summative tasks in consecutive weeks → suggest redistributing
- All tasks in the same mode → suggest adding variety
- Standards with no assessment task → flag the gap

> "Here's the assessment schedule. I've noted [any imbalance] — would you
> like to adjust the timing or add a task to cover [gap]?"

---

## Step 5: Offer next step

> "With the schedule in place, a natural next step is building a rubric for
> one of these tasks — or if you haven't designed the individual tasks in
> detail yet, the Assessment Outline skill can help with that first."

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
