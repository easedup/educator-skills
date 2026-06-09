# EasedUP URL Patterns — UK National Curriculum

Base URL: `https://uk-curriculum.easedup.com`
MCP URL:  `https://uk-curriculum.easedup.com/mcp`

Append `.md` to any curriculum page path to get the clean Markdown version.
Always fetch the `.md` version, not the HTML page.

---

## English
```
/english/year-1.md
/english/year-2.md
/english/years-3-and-4.md
/english/years-5-and-6.md
/english/stage-3.md      (Years 7–9)
/english/stage-4.md      (Years 10–11)
```

## Mathematics
```
/mathematics/year-1.md
/mathematics/year-2.md
/mathematics/year-3.md
/mathematics/year-4.md
/mathematics/year-5.md
/mathematics/year-6.md
/mathematics/stage-3.md  (Years 7–9)
/mathematics/stage-4.md  (Years 10–11)
```

## Science
```
/science/year-1.md
/science/year-2.md
/science/year-3.md
/science/year-4.md
/science/year-5.md
/science/year-6.md
/science/stage-3.md      (Years 7–9)
/science/stage-4.md      (Years 10–11)
```

## Other subjects
These subjects use a primary / secondary split rather than individual year levels.

```
/art-and-design/primary.md          /art-and-design/secondary.md
/computing/primary.md               /computing/secondary.md
/design-and-technology/primary.md   /design-and-technology/secondary.md
/geography/primary.md               /geography/secondary.md
/history/primary.md                 /history/secondary.md
/music/primary.md                   /music/secondary.md
/physical-education/primary.md      /physical-education/secondary.md
/languages/primary.md               /languages/secondary.md
/citizenship/secondary.md
```

---

## Key Stage reference

| Key Stage | Years | Age range |
|-----------|-------|-----------|
| KS1 | Years 1–2 | 5–7 |
| KS2 | Years 3–6 | 7–11 |
| KS3 | Years 7–9 (stage-3) | 11–14 |
| KS4 | Years 10–11 (stage-4) | 14–16 |

When a teacher refers to a Key Stage rather than a year, fetch the corresponding
stage file/s above.

---

## Notes

- The `.md` files include a `queried:` timestamp in the frontmatter — cite this
  when referencing standards so teachers know how current the content is.
- The UK National Curriculum does not use content codes — standards are written
  in prose only. Quote directly rather than citing a code.
- If a URL returns 404, use the MCP `get_all` tool or check
  `https://uk-curriculum.easedup.com` for valid paths.
