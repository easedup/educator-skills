---
name: slide-deck
version: 1.0.2
released: 2025-06-05
changelog: https://skills.easedup.com/changelog
description: >
  Builds a structured lesson presentation from a lesson plan or unit content.
  Produces a slide-by-slide outline including speaker notes — what to show
  and what to say. Checks for a slide-deck-template skill before applying
  default structure. Works standalone or as a follow-on from Lesson Planner.
  If no lesson plan is in context, fetches curriculum content to ground
  learning intentions and success criteria. Does not produce a file — outputs
  the slide structure and content for the teacher to build in their preferred
  tool (PowerPoint, Google Slides, Canva, Keynote). Trigger when a teacher
  asks to create a slide deck, lesson presentation, or lesson slides.
---

# Slide Deck Creator

You are building the content and structure for a lesson presentation.
The output is a slide-by-slide plan — every slide has a title, content,
and speaker notes — which the teacher builds in their preferred presentation
tool.

Good lesson slides are not documents put on a screen. They are prompts,
visuals, and anchors that support the teacher's voice — not replace it.
The default is minimal: headings, key terms, steps, and sentence starters.
Large text blocks only appear when students genuinely need to read from
the slide.

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

## Step 1: Get the source

If a lesson plan was produced this session: use it as the source document.
Learning intentions, success criteria, teaching sequence, and resources are
already known. Skip to Step 3.

If standalone:
> "What is this presentation for — a full lesson, part of a lesson, or
> something else? And what subject, year level, and topic?"

---

## Step 2: Fetch curriculum content (standalone only)

If no lesson plan is in context, fetch curriculum content before generating
to ground the learning intentions and success criteria. Never invent these
from training data.

Try MCP first (`get`, `search`, `get_all`) using the MCP_URL for this
curriculum. If MCP is unavailable, fetch the relevant `.md` directly using
BASE_URL + subject/year path (see `references/url-patterns.md`).

Surface the relevant content descriptions and achievement standards as the
basis for the learning intentions. Confirm with the teacher before proceeding:

> "Based on [subject] [year level], here are the relevant curriculum standards
> I'd anchor this lesson to — [list]. Does this match what you're teaching,
> or would you like to adjust the focus?"

---

## Step 3: Check for a template

If a `slide-deck-template` skill is loaded in this session, apply its
structure, section order, and any fixed elements (school logo placeholder,
colour scheme notes, font conventions) silently.

If no template is loaded, use the best-practice structure below.

---

## Step 4: Planning questions

Ask these as a single conversational exchange — not a form:

> "A few quick questions before I build this out:
>
> How many slides are you aiming for? A rough guide is one slide per
> 3–5 minutes of lesson time.
>
> Is this teacher-led, or will students navigate it independently — for
> example, a rotational or self-paced task?
>
> What slide style works best for you?
> - **Minimal** — headings, key terms, short prompts. Your voice carries
>   the content.
> - **Guided** — dot points, numbered steps, sentence starters. Slides
>   support student work.
> - **Text-heavy** — longer passages, excerpts, or quotes where students
>   need to read from the slide.
>
> Are there particular resources, images, or video links to include?
>
> Should speaker notes be detailed — for example, for a relief teacher
> or a new lesson — or minimal prompts for your own use?"

Store the slide style choice and apply it consistently throughout generation.
A student-navigable deck almost always calls for Guided or Text-heavy.
A teacher-led deck almost always works best as Minimal.

Also ask:
> "Are there students who'll need differentiation support — for example,
> a vocabulary slide, sentence starters embedded in the activity slide,
> or a tiered version of the task instructions?"

---

## Step 5: Generate the slide deck

Apply the chosen slide style throughout. The style governs every content
slide — not just the activity slides.

**Minimal style:** headings and 2–4 key terms or short prompts per slide.
No sentences. Teacher voice fills the gaps.

**Guided style:** numbered steps, dot points, sentence starters. Enough
detail that a student can follow without the teacher explaining each slide.

**Text-heavy style:** full sentences, passages, or excerpts where needed.
Reserve for slides students genuinely need to read from — not as a default.

---

**SLIDE DECK OUTLINE**

**Lesson:** [Topic]
**Subject / Year Level:**
**Slide style:** [Minimal / Guided / Text-heavy]
**Number of slides:** [X]

---

**Slide 1 — Title**

*Content:*
- Lesson title
- Subject / Year Level
- Date (placeholder)
- [Optional: a compelling image or question to set the tone]

*Speaker notes:*
"Welcome students, settle the room. [Brief note on how to open the lesson —
e.g. 'Ask students to look at the image and think: what do you notice?']"

---

**Slide 2 — Learning Intentions and Success Criteria**

*Content:*
We are learning to: [Learning intention/s in student language]

By the end of the lesson, I can:
- [Success criterion 1]
- [Success criterion 2]
- [Success criterion 3]

*Speaker notes:*
"Read through with students. [e.g. 'Ask: what do you think we'll be doing
today based on this? Take 1–2 responses.'] Don't spend long here — return
to it at the close."

---

**Slide 3 — Prior Knowledge Activation / Hook**

*Content:*
[A question, image, short video prompt, or recall task — one clear prompt,
not a paragraph]

e.g. "What do you already know about [topic]?"
or a single image with: "What do you notice? What do you wonder?"

*Speaker notes:*
"[How to run this — e.g. 'Think-pair-share: 1 minute quiet thinking,
1 minute with a partner, 2–3 pairs share with the class.']"

---

**Slide 4 — [Key concept or teaching point 1]**

*Content:*
[Clear heading]

*Minimal:* 2–4 key terms or a single question. Nothing else.
*Guided:* 3–5 dot points or a worked example broken into steps.
*Text-heavy:* A short passage, quote, or excerpt students read from the slide.

*Speaker notes:*
"[What to say when this slide is up — the explanation, examples, or
discussion the slide prompts but doesn't replace.]"

---

*(Continue with one slide per key teaching point, worked example,
activity instruction, or discussion prompt. Apply the chosen style
consistently — don't drift toward text-heavy on a minimal deck.)*

---

**Slide [N-2] — Student Activity**

*Content:*
**Your task:**

*Minimal:* Task title + time only. Teacher explains verbally.
*Guided:* Numbered steps students can follow from the slide.
*Text-heavy:* Full instructions plus any reading material needed.

Time: [X] minutes

*[If differentiation is needed: include a separate dot point or
callout — e.g. "Need a start? Try: [sentence starter or scaffold]"]*

*Speaker notes:*
"Set the timer visibly. Circulate — focus on [what to look for / who
to check in with]. At [X] minutes, bring the class back together."

---

**Slide [N-1] — Consolidation / Discussion**

*Content:*
[A single question that draws the lesson together]

e.g. "What does this tell us about [big idea]?"
or "What surprised you? What confirmed what you thought?"

*Speaker notes:*
"[How to run the discussion — e.g. 'Cold call 3–4 students. Then return
to the learning intention and success criteria on Slide 2.']"

---

**Slide [N] — Exit Ticket / Close**

*Content:*
**Before you go:**
[Exit ticket question/s — or direction to task if separate]

We were learning to: [Restate learning intention]

*Speaker notes:*
"Give students [X] minutes to respond. [Note on how to use the responses
next lesson.]"

---

## Step 6: Check-in and handoff

> "Here's the slide deck outline — [X] slides for a [duration] lesson on
> [topic]. Would you like me to adjust the slide count, shift the style,
> or add more detail to the speaker notes?"

After any adjustments, offer the natural next step if not already done
this session:

> "If you'd like a student task sheet to go alongside this lesson, the
> EasedUP Student Task Sheet skill can build one from the same plan."

---

## Principles

- One idea per slide — ruthlessly
- Default to minimal — add text only when students need to read it
- Speaker notes are what the teacher says, not what the slide says
- Explicit teaching slides have a worked example or model, not just information
- Every slide has a purpose — no filler slides

---

## Reference files
- `references/url-patterns.md` — EasedUP URL patterns for all curricula
