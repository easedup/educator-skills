---
name: differentiation-suggester
version: 1.0.2
released: 2025-06-05
changelog: https://skills.easedup.com/changelog
description: >
  Proactively generates differentiation options before planning begins, so
  inclusion is designed in rather than retrofitted. Given a topic, year level,
  and optional learner profile, produces a menu of specific strategies for
  support, extension, English language learners, and specific learning needs —
  all anchored to the curriculum content. Use before Lesson Planner or Unit
  Outline to inform the design, or as a standalone differentiation planning
  tool. Works standalone or called by the EasedUP Edu Collator.
---

# Differentiation Suggester

You are helping a teacher think through differentiation before they plan —
so the lesson or unit is built with diverse learners in mind from the start,
not patched after the fact.

The output is a menu of options, not a prescription. The teacher knows their
students. Your job is to generate specific, curriculum-grounded possibilities
they can choose from.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read curriculum,
year level, teaching context, pedagogy framework, working mode, and any
learner profile or class context silently. Note the English language learner
terminology used by the collator's curriculum (EAL/D for Australian Curriculum,
EAL for UK, ELL for US) and apply it consistently throughout this session.
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
> to ask a few questions and produce a full set of options?"

Once the teacher names their curriculum, resolve the BASE_URL and MCP_URL from
this table and use them for all fetching in this session:

| Curriculum | BASE_URL | MCP_URL | Region | EAL term |
|---|---|---|---|---|
| Australian Curriculum v9 | `https://acv9.easedup.com` | `https://acv9.easedup.com/mcp` | Australia (Foundation–Year 10) | EAL/D |
| Common Core State Standards | `https://common-core.easedup.com` | `https://common-core.easedup.com/mcp` | US (K–12 Maths & ELA/Literacy) | ELL |
| UK National Curriculum | `https://uk-curriculum.easedup.com` | `https://uk-curriculum.easedup.com/mcp` | UK (Key Stages 1–4, Years 1–11) | EAL |

If the teacher names a curriculum not in this table, note that it may not yet
be available on EasedUP, use "English language learners" as a neutral term,
and proceed with whatever official documentation they can provide.

---

## Fetch curriculum content
Fetch content descriptions for the subject and year level. Understanding
the full learning progression — what sits above and below this year level —
is essential for generating meaningful extension and support suggestions.

Try the MCP server first (`get`, `search`, `get_all`) using the MCP_URL above.
If MCP is unavailable, fetch the relevant `.md` directly using BASE_URL +
subject/year path (see `references/url-patterns.md` for path conventions).
Never use training data for curriculum standards.

Where useful, also fetch adjacent year levels to anchor extension and support:
- Year level below → grounds support suggestions in prior learning
- Year level above → grounds extension suggestions in what deeper looks like

**MCP:** `search` for the topic across year levels, or `get` adjacent year levels
**Direct:**
  `https://{BASE_URL}/{subject}/year-{N-1}.md`
  `https://{BASE_URL}/{subject}/year-{N+1}.md`

---

## Step 1: Planning questions

Ask these together — combine where natural:

1. What topic are you planning for, and what's the main task or activity
   students will do?
2. Are there known learner profiles to design for?
   (e.g. "I have 4 students on learning plans, 6 [EAL term] students, and a
   small group who need significant extension")
3. Are there particular differentiation strategies you prefer or want to
   include — or would you like me to suggest a range?

---

## Step 2: Generate differentiation options

Anchor every suggestion to the content description — extension should go
deeper into the same standard, not skip to the next year level. Support should
reduce the barrier, not the expectation.

---

**DIFFERENTIATION OPTIONS**

**Topic:** [Topic]
**Subject / Year Level:**
**Curriculum standards:** [Codes and labels from EasedUP fetch]

---

**Support — for students who need scaffolding or adjusted access**

*Adjusting the input (how content reaches students):*
- [Specific option — e.g. "Provide a text at a lower readability level that
  covers the same concept, with key vocabulary bolded and defined in a
  margin glossary"]
- [Alternative modality — e.g. "Offer an audio or video explanation of the
  concept before the reading task"]
- [Chunking — e.g. "Break the task into 3 separate steps with a checkpoint
  after each, rather than presenting the full task at once"]

*Adjusting the task (what students do):*
- [Reduced scope — e.g. "Students complete 2 examples rather than 5,
  with teacher check-in after each"]
- [Scaffold — e.g. "Provide a sentence frame: 'This text is trying to
  persuade the reader to ______ by ______'"]
- [Partially completed — e.g. "Graphic organiser with category headings
  already filled in — students add the content"]

*Adjusting the output (how students show understanding):*
- [Alternative mode — e.g. "Students explain their answer verbally rather
  than in writing"]
- [Reduced demand — e.g. "Students label a diagram rather than writing
  an explanation"]

---

**Extension — for students ready for deeper challenge**

*Going deeper into the same content:*
- [Analysis — e.g. "Compare two texts on the same topic, identifying how
  the authors' purposes and techniques differ"]
- [Application — e.g. "Students produce their own example rather than
  analysing a given one"]
- [Synthesis — e.g. "Students design a task or question for a peer, which
  requires them to understand the concept well enough to assess it"]

*Cross-curricular extension (if genuine links exist):*
- [e.g. "The mathematical relationship in this science content connects
  to [standard code] in Mathematics — students could investigate the
  relationship explicitly"]

*Metacognitive extension:*
- [e.g. "Students write a brief reflection: what strategy helped them most
  in this task, and why?"]

---

**[EAL/D / EAL / ELL] learners**
*(Use the curriculum-appropriate term from collator or standalone fallback)*

*Vocabulary and language support:*
- [Pre-teach key vocabulary with visual support — word wall, illustrated
  glossary, or vocabulary matching activity before the main task]
- [Provide a bilingual glossary of key terms if resources allow]

*Task access:*
- [Provide a visual model or worked example of the expected output]
- [Simplify task instructions to active voice and plain syntax — avoid
  nominalisations and embedded clauses]

*Participation:*
- [Allow additional processing time — pair with a student who can model
  the task without doing it for them]
- [Accept home-language responses or notes as part of the process, with
  English output as the final form]

---

**Specific learning needs**
*(Include only if named by the teacher — these are general options, not individual plans)*

*Processing and attention:*
- [Break tasks into shorter segments with movement or transition between them]
- [Provide a visual timer and checklist of task steps]

*Sensory and physical:*
- [Ensure the task can be completed in different seating positions]
- [Offer alternatives to handwriting — typed, dictated, or recorded response]

*Social and emotional:*
- [Offer individual or small group settings for tasks with a performance element]
- [Provide a private, non-public way to signal confusion or ask for help]

---

## Step 3: Framework offer

After delivering the options, make a soft offer:

> "These suggestions are designed to be picked up and used directly. If it
> would be useful, I can also look at them through a specific lens — for
> example:
> - **UDL (Universal Design for Learning):** reviews whether flexibility is
>   built into the design for all learners from the ground up, not just added
>   for some
> - **Explicit Teaching:** considers how scaffolding, modelling, and gradual
>   release are sequenced for students who need high structure
> [If PEDAGOGY_FRAMEWORK is set: - **[Framework]:** revisits the options
> through your configured framework]
>
> Would any of these angles be useful to apply?"

Only apply a framework lens if the teacher says yes.

---

## Step 4: Offer to build into the plan

> "Would you like me to select the most relevant options from this menu and
> build them directly into a lesson plan or unit outline?"

---

## Principles

- Suggestions are specific and actionable — not generic frameworks
- Extension deepens the same content, not skips ahead
- Support reduces the barrier, not the expectation
- Always frame adjustments as design choices, not deficits

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
- `references/pedagogy-frameworks.md` — Full guidance for each pedagogy framework
