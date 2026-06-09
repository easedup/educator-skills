# Educator Skills

Agent skills for teachers — curriculum-aligned, voice-aware, and built for real classrooms.

## Quickstart

### Claude (claude.ai)

Requires a **Pro, Max, Team, or Enterprise** plan with code execution enabled.

1. [Download this repository as a ZIP](https://github.com/nickec86/educator-skills/archive/refs/heads/main.zip) and unzip it on your computer.
2. In [claude.ai](https://claude.ai), open **Settings → Features → Custom Skills**.
3. For each skill you want, zip its folder (e.g. `skills/planning/lesson-planner/`) and upload it.

Once installed, start any planning session by asking Claude to use the **edu-collator** — it sets your curriculum context and coordinates everything else.

> See [Using Skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude) for full instructions.

### ChatGPT

These skills use Anthropic's [Agent Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) format. ChatGPT has its own skills system — see [Skills in ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt) for how to configure comparable capabilities there.

### Claude Code (terminal)

```bash
npx skills@latest add nickec86/educator-skills
```

Pick the skills you want and which coding agents to install them on.

## Reference

### Collator

The master orchestrator. Load this first.

- **[edu-collator](./skills/collator/edu-collator/SKILL.md)** — Entry point for any educational planning task. Sets curriculum context, selects the right downstream skills, and coordinates the full workflow.

### Assessment

Skills for designing tasks, building rubrics, and checking student understanding.

- **[assessment-outline](./skills/assessment/assessment-outline/SKILL.md)** — Writes a formal assessment task outline with task description, conditions, mode, curriculum links, and a rubric pointer. Always fetches live curriculum content from EasedUP.
- **[rubric-builder](./skills/assessment/rubric-builder/SKILL.md)** — Builds a criteria-based marking rubric with descriptors drawn directly from achievement standards. Works standalone or as a direct follow-on from Assessment Outline.
- **[exit-ticket](./skills/assessment/exit-ticket/SKILL.md)** — Generates targeted end-of-lesson formative assessment questions matched to the lesson's learning intention. Supports written, multiple choice, discussion, and self-assessment formats.
- **[feedback-comment-bank](./skills/assessment/feedback-comment-bank/SKILL.md)** — Generates a reusable bank of written feedback phrases organised by rubric criterion and grade band, grounded in achievement standards language.

### Planning

Skills for designing lessons, units, and classroom resources.

- **[lesson-planner](./skills/planning/lesson-planner/SKILL.md)** — Creates a single complete, curriculum-aligned lesson plan with goals, success criteria, a teaching sequence, differentiation, resources, and assessment.
- **[unit-outline](./skills/planning/unit-outline/SKILL.md)** — Creates a high-level unit outline — scope and sequence, big ideas, essential questions, curriculum links, and assessment overview. Use before expanding to a full Unit of Work.
- **[unit-of-work](./skills/planning/unit-of-work/SKILL.md)** — Creates a complete, ready-to-teach unit of work with every lesson planned in full detail. Calls Lesson Planner internally for each lesson.
- **[casual-relief-plan](./skills/planning/casual-relief-plan/SKILL.md)** — Generates a complete, self-contained day pack for a casual or relief teacher covering timetable, lesson notes, student welfare information, and emergency contacts.
- **[slide-deck](./skills/planning/slide-deck/SKILL.md)** — Builds a structured lesson presentation from a lesson plan, producing a slide-by-slide outline with speaker notes.
- **[student-task-sheet](./skills/planning/student-task-sheet/SKILL.md)** — Translates a teacher's lesson plan or assessment task into a clear, student-facing document with instructions, scaffolds, and success criteria in student language.

### Differentiation

Skills for reviewing and designing inclusive, differentiated learning experiences.

- **[differentiation-reviewer](./skills/differentiation/differentiation-reviewer/SKILL.md)** — Audits an existing lesson plan or unit for differentiation and inclusion gaps, providing specific actionable suggestions without rewriting the whole plan.
- **[differentiation-suggester](./skills/differentiation/differentiation-suggester/SKILL.md)** — Proactively generates a menu of differentiation strategies before planning begins — support, extension, English language learners, and specific learning needs.

### Inquiry

Skills for designing inquiry-based and project-based learning units.

- **[pbl-unit](./skills/inquiry/pbl-unit/SKILL.md)** — Creates a complete project-based learning (PBL) unit structured around a driving question, real-world context, inquiry phases, milestones, and a public product.
- **[ibl-unit](./skills/inquiry/ibl-unit/SKILL.md)** — Creates a complete inquiry-based learning (IBL) unit structured around a central inquiry question, an inquiry cycle, and student-generated understanding. Supports structured, guided, and open inquiry models.

### Communication

Skills for writing teacher-to-family and school communications.

- **[parent-comms](./skills/communication/parent-comms/SKILL.md)** — Drafts polished parent-facing communications (newsletters, curriculum updates, excursion notes, learning updates) in the teacher's own voice.
- **[parent-curriculum-explainer](./skills/communication/parent-curriculum-explainer/SKILL.md)** — Translates curriculum content into plain English for families — what students are learning, why it matters, and how families can support at home.
- **[report-comment](./skills/communication/report-comment/SKILL.md)** — Drafts personalised report comments in the teacher's own voice, aligned to achievement standards language. The teacher provides the grade judgment — the skill never infers one.
- **[voice-style-capture](./skills/communication/voice-style-capture/SKILL.md)** — Learns a teacher's written voice from examples so that report comments and communications sound like the teacher wrote them. Run once to produce a voice profile used by Report Comment and Parent Comms.
