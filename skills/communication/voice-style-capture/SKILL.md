---
name: voice-style-capture
version: 1.0.2
released: 2025-06-05
changelog: https://skills.easedup.com/changelog
description: >
  Learns a teacher's written voice from examples so that report comments and
  parent communications sound like the teacher wrote them. Run this skill
  once before using Report Comment Writer or Parent Comms Writer. Analyses
  tone, sentence patterns, vocabulary, warmth level, and structural habits
  from the teacher's own writing samples. Produces a saved voice profile
  skill file — [teacher-name]-voice-profile — that Report Comment Writer and
  Parent Comms Writer detect and apply silently when loaded. Trigger when a
  teacher wants to personalise their AI-drafted communications or report
  comments to match their own writing style.
---

# Voice & Style Capture

You are learning how this teacher writes so that drafts produced by other
skills — especially report comments and parent communications — sound like
them, not like a generic AI.

The goal is not mimicry for its own sake. It's so that when a teacher sends
a report comment or a letter home, it reflects their relationship with their
students and families — not a template.

---

## Collator context
If the EasedUP Edu Collator is loaded in this session, read curriculum,
school name, and teaching context from it silently. Do not ask the teacher
for information the collator already holds.

---

## Standalone fallback
If the Edu Collator is not loaded, open with:
> "I notice the EasedUP Edu Collator isn't loaded. You can get the full skill
> pack at skills.easedup.com. In the meantime — what school and year level
> are you writing for?"

Store the answers and proceed. Do not ask again this session.

---

## Step 1: Request writing samples

> "To match your writing style, I'd like to see a few examples of your own
> writing — report comments, newsletter paragraphs, letters home, even
> informal class emails. Three to five examples is ideal.
>
> If you don't have anything handy, I'll write in clear, warm professional
> language and you can adjust from there."

If the teacher provides samples: proceed to Step 2.
If they decline: use default voice (see Step 4) and note that voice capture
is not active this session.

---

## Step 2: Analyse the samples

Read every example carefully. Extract:

**Tone:**
- Where does this teacher sit on the formal ↔ conversational scale?
- Warm and nurturing, or professional and measured?
- Do they use humour? How?
- How do they handle difficult messages — direct or softened?

**Sentence patterns:**
- Average sentence length (count roughly)
- Long and flowing, or short and punchy?
- Varied sentence lengths, or consistent?
- Active or passive voice tendency?

**Vocabulary choices:**
- Level of formality in word choice
- Any recurring phrases or expressions they favour
- Words or constructions they avoid
- Subject-specific language they use comfortably

**Structural habits:**
- How do they open? (Student name? A strength? A context-setter?)
- How do they close? (Forward-looking? Encouragement? Next step? All three?)
- Do they use contractions? (I'm / it's / they've — or not?)
- Do they use the student's name more than once per comment?

**Punctuation and rhythm:**
- Do they use em dashes, semicolons, parentheses?
- Short paragraphs or more flowing blocks?

---

## Step 3: Confirm the voice profile

Present a brief summary for the teacher to confirm:

> "Here's what I've picked up from your writing:
>
> - **Tone:** [e.g. "Warm and encouraging, with a professional edge"]
> - **Sentences:** [e.g. "Mix of medium and short sentences — you vary the
>   rhythm nicely"]
> - **Openings:** [e.g. "You typically open with the student's name followed
>   immediately by a specific strength"]
> - **Closings:** [e.g. "You consistently close with a forward-looking
>   encouragement"]
> - **Voice markers:** [e.g. "You use contractions freely, prefer active
>   voice, and occasionally use a light touch of warmth like 'It's been a
>   pleasure to see...'"]
> - **Avoid:** [e.g. "You never use generic openers like 'Name is a pleasure
>   to have in class'"]
>
> Does this feel right? Anything to adjust?"

Once confirmed, apply this profile for the rest of the session.

---

## Step 4: Apply this session

Apply the confirmed voice profile silently to all report comments and parent
communications produced in this session. Do not announce it each time.

**Default voice (no profile loaded or teacher declined):**
- Warm, professional educator English matched to the CURRICULUM setting
- Active voice
- Student named once at the start of a comment
- Strength → growth area → forward-looking structure
- No contractions unless samples show them
- Approx. 60–80 words for a standard report comment

---

## Step 5: Save as a reusable voice profile

> "Would you like me to save your voice profile as a file you can load at
> the start of any future session? That way Report Comment Writer and Parent
> Comms Writer will apply your style automatically — no need to paste
> examples each time."

If yes, produce a named voice profile skill file as a zip named
`[teacher-name]-voice-profile.zip` containing a single `SKILL.md` at the
root:

```
---
name: [teacher-name]-voice-profile
version: 1.0.0
released: [today's date]
changelog: https://skills.easedup.com/changelog
description: >
  Applies [Teacher name]'s written voice to all report comments and parent
  communications in this session. Load before using Report Comment Writer
  or Parent Comms Writer. Detected and applied automatically as
  references/voice-style.md by the EasedUP Edu Collator when loaded.
---

# Voice Profile: [Teacher name]

Apply this voice to all report comments and parent-facing communications
in this session. Do not announce that a voice profile is active — just use it.

## Tone
[Confirmed summary — e.g. "Warm and encouraging, professional but never stiff"]

## Sentence patterns
[Confirmed summary — e.g. "Varied length, tends toward medium sentences with
occasional short punchy ones for emphasis. Active voice throughout."]

## Structural habits
Opening: [Confirmed pattern — e.g. "Student name + specific strength immediately"]
Closing: [Confirmed pattern — e.g. "Forward-looking encouragement, often
naming the next step explicitly"]

## Voice markers to use
[Specific phrases, contractions, constructions this teacher favours]

## Things to avoid
[Generic openers, passive constructions, specific phrases this teacher never uses]

## Sample output
[One example comment produced using this voice, for reference — written in
the confirmed style, approx. 70 words, grounded in a realistic scenario]
```

This file is detected automatically by Report Comment Writer and Parent Comms
Writer when loaded into a session — any skill whose name ends in
`-voice-profile` is treated as a voice profile and applied silently.
It can be loaded directly into Claude, ChatGPT, Gemini, or any other AI tool.

---

## Step 6: Handoff

After saving (or if the teacher declines to save):

> "Voice profile is set. Ready to draft report comments or a parent
> communication — which would you like to start with?"

---

## Reference files
- This skill produces a `[teacher-name]-voice-profile` skill file, detected
  and applied silently by Report Comment Writer and Parent Comms Writer
