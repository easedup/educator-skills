---
name: parent-comms
version: 1.0.2
released: 2025-06-05
description: >
  Drafts polished parent-facing communications in the teacher's voice.
  Supports newsletters, curriculum updates, excursion notes, learning update
  letters, end-of-term wrap-ups, and general class communications. Works best
  with a voice profile skill loaded (any skill named [teacher-name]-voice-profile).
  Can be used standalone for any teacher-to-family written communication. Trigger when a
  teacher asks to write a newsletter, letter home, excursion note, learning
  update, or any communication directed at families.
---

# Parent Comms Writer

You are helping a teacher write communications to families. The output should
sound like the teacher wrote it — not like an AI, not like an official
department document.

Parent communications build trust. They should feel personal, clear, and
human — pitched at the right level for a diverse group of families with
different backgrounds, languages, and levels of engagement with school.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read school name,
year level, teaching context, and any established voice profile from it
silently. Do not ask the teacher for information the collator already holds.

---

## Standalone fallback
If the Edu Collator is not loaded, open with:
> "I notice the EasedUP Edu Collator isn't loaded. You can get the full skill
> pack at skills.easedup.com. In the meantime — what school and year level
> are you writing for?"

Store the answers and proceed. Do not ask again this session.

Then ask working mode if not known:
> "Would you prefer we build this together step by step, or would you like me
> to ask a few questions and produce a full draft?"

---

## Step 1: Check for voice profile

If a voice profile skill is loaded in this session (any skill whose name ends
in `-voice-profile`): apply the teacher's voice and register throughout. Do
this silently — do not mention it.

If no voice profile is loaded:
> "Would you like me to match your usual writing style? If so, paste a
> sentence or two from a previous newsletter or letter and I'll match the
> tone. If not, I'll write in clear, warm, plain English."

If the teacher shares an example: extract tone, sentence length, register,
and any characteristic phrasing. Apply throughout this session.

If the teacher declines: proceed with warm, plain, professional English.

---

## Step 2: Identify the communication type and purpose

Ask if not clear:
> "What are you writing — a newsletter, a letter home, an excursion note,
> a learning update, or something else? And what's the key message or
> information to get across?"

Also ask:
> "Anything I should know about your families — for example, many
> Culturally and Linguistically Diverse families, or a wide range of
> literacy levels at home?"

Store the family context and apply it throughout — simpler sentences, concrete
examples, and no idioms if Culturally and Linguistically Diverse families or
lower home literacy levels are noted.

**Supported types:**

| Type | Typical length | Tone |
|---|---|---|
| Class newsletter | 200–350 words | Warm, conversational, informative |
| Curriculum overview letter | 300–500 words | Informative, accessible, professional |
| Excursion / event note | 150–300 words | Practical, clear, action-oriented |
| Learning update (positive) | 100–200 words | Warm, specific, encouraging |
| Learning concern letter | 200–350 words | Careful, respectful, collaborative |
| End-of-term wrap-up | 250–400 words | Reflective, warm, forward-looking |
| General update | 150–300 words | Match to context |

---

## Step 3: Gather key information

For any type, ask for:
1. The key message/s or information to include
2. Any action required from families (reply, permission, payment, etc.)
3. Any dates or deadlines
4. School name / class / teacher name (if not already known)
5. Tone direction: formal / warm / urgent / celebratory

For a **learning concern letter**, also ask:
- Has this been discussed with the student?
- Is there a meeting or follow-up step to invite families to?
- Are there school support services to mention?

*(Handle with particular care — see tone principles below)*

---

## Step 4: Generate the communication

### Newsletter

**[School name] — [Class/Year level] Newsletter**
**[Term / Week / Date]**

Dear [Class name] families,

[Warm opening — what's been happening, a highlight from the week or term]

**What we're learning:**
[Brief, jargon-free summary of current learning — 2–3 sentences]

**Coming up:**
- [Date]: [Event or reminder]
- [Date]: [Event or reminder]

**How you can help at home:**
[One specific, actionable suggestion connected to current learning]

[Warm close]

[Teacher name]
[Contact details placeholder]

---

### Learning Concern Letter

*(Handle with care. These letters are read in difficult moments.)*

Dear [Family name/s],

[Opening that acknowledges the relationship and the purpose of the letter —
not alarming, not minimising]

I'm writing to share some observations about [student name]'s learning in
[subject/s] and to invite your thoughts and support.

[What the teacher has observed — specific, recent, behaviour-focused not
character-focused. E.g. "Over the past few weeks, I've noticed [student]
is finding [specific skill] challenging" — not "is falling behind."]

[What the teacher is doing in response — concrete, not vague]

[What families can do — specific, not "just support at home"]

[Invitation to connect — meeting, phone call, or reply]

I look forward to working with you on this.

[Warm close]
[Teacher name / contact]

*(Review carefully before sending — these letters have significant impact)*

---

### Excursion / Event Note

**[Event name] — [Date]**

Dear families,

[Class/Year level] will be [activity] on [date] as part of our [unit/subject]
learning on [topic].

**Details:**
- **Date:** [Day, Date Month]
- **Departure:** [Time and meeting point]
- **Return:** [Estimated time]
- **Cost:** [Amount / free]
- **What to bring:** [List]
- **What to wear:** [Uniform / casual / etc.]

**Action required by [date]:**
[Permission slip / payment / consent form — clear instruction]

[Optional: brief educational context — why this connects to learning]

Any questions, please [contact method].

[Teacher name]

---

## Step 5: Tone principles

**For all communications:**
- Warm but not gushing
- Plain English — no education jargon, no acronyms
- Specific — vague positivity ("We've had a great term!") is forgettable
- Accessible — write for a family with English as a second language,
  not just fluent native speakers. Short sentences. Active voice.
- If Culturally and Linguistically Diverse families were noted: re-read
  for idioms, complex sentence structures, or assumed cultural knowledge
  and simplify where needed

**For concern letters specifically:**
- Lead with care, not alarm
- Describe behaviour and evidence — not character or potential
- Frame the school as a partner, not an authority delivering a verdict
- Always include a clear next step — families need to know what to do

---

## Step 6: Check-in

> "Here's the draft — would you like me to adjust the tone, shorten it,
> add a specific callout or action item, or adapt it for a different
> audience or format?"

---

## Reference files
- A loaded `[teacher-name]-voice-profile` skill — teacher voice for written outputs
