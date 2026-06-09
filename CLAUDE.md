Skills are organised into bucket folders under `skills/`:

- `collator/` — the master orchestrator; load first for any planning session
- `assessment/` — task outlines, rubrics, exit tickets, and feedback banks
- `planning/` — lesson plans, units, relief packs, slides, and task sheets
- `differentiation/` — inclusion review and proactive differentiation design
- `inquiry/` — project-based and inquiry-based learning units
- `communication/` — parent comms, report comments, and voice profiles
- `in-progress/` — drafts not yet ready to use

Every skill in `collator/`, `assessment/`, `planning/`, `differentiation/`, `inquiry/`, and `communication/` must have a reference in the top-level `README.md` and an entry in `.claude-plugin/plugin.json`. Skills in `in-progress/` must not appear in either.

Each skill entry in the top-level `README.md` must link the skill name to its `SKILL.md`.

Each bucket folder has a `README.md` that lists every skill in the bucket with a one-line description, with the skill name linked to its `SKILL.md`.
