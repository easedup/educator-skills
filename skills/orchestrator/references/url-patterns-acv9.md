# EasedUP URL Patterns — Australian Curriculum v9

Base URL: `https://acv9.easedup.com`
MCP URL:  `https://acv9.easedup.com/mcp`

Append `.md` to any curriculum page path to get the clean Markdown version.
Always fetch the `.md` version, not the HTML page.

---

## English
```
/english/foundation-year.md
/english/year-1.md  through  /english/year-10.md
```

## Mathematics
```
/maths/foundation-year.md
/maths/year-1.md  through  /maths/year-10.md
```

## Science
```
/science/foundation-year.md
/science/year-1.md  through  /science/year-10.md
```

## HASS (Foundation–Year 6)
```
/hass/foundation-year.md
/hass/year-1.md  through  /hass/year-6.md
```

## HASS Specialist Subjects (Years 7–10)
```
/hass-civics-and-citizenship/year-7.md  through  year-10.md
/hass-economics-and-business/year-7.md  through  year-10.md
/hass-geography/year-7.md  through  year-10.md
/hass-history/year-7.md  through  year-10.md
```

## Health and Physical Education
```
/hpe/foundation-year.md
/hpe/years-1-and-2.md
/hpe/years-3-and-4.md
/hpe/years-5-and-6.md
/hpe/years-7-and-8.md
/hpe/years-9-and-10.md
```

## Technologies
```
/tech-design-and-technologies/foundation-year.md
/tech-design-and-technologies/years-1-and-2.md
/tech-design-and-technologies/years-3-and-4.md
/tech-design-and-technologies/years-5-and-6.md
/tech-design-and-technologies/years-7-and-8.md
/tech-design-and-technologies/years-9-and-10.md

/tech-digital-technologies/foundation-year.md
/tech-digital-technologies/years-1-and-2.md
/tech-digital-technologies/years-3-and-4.md
/tech-digital-technologies/years-5-and-6.md
/tech-digital-technologies/years-7-and-8.md
/tech-digital-technologies/years-9-and-10.md
```

## The Arts
```
/arts-dance/foundation-year.md
/arts-dance/years-1-and-2.md
/arts-dance/years-3-and-4.md
/arts-dance/years-5-and-6.md
/arts-dance/years-7-and-8.md
/arts-dance/years-9-and-10.md

/arts-drama/        (same year pattern as above)
/arts-media-arts/   (same year pattern as above)
/arts-music/        (same year pattern as above)
/arts-visual-arts/  (same year pattern as above)
```

## Languages
```
/languages/foundation-year.md
/languages/years-1-and-2.md  through  /languages/years-9-and-10.md
```

---

## Notes

- The `.md` files include a `queried:` timestamp in the frontmatter — cite this
  when referencing standards so teachers know how current the content is.
- If a URL returns 404, that subject/year combination may not exist. Use the
  MCP `get_all` tool or check `https://acv9.easedup.com` for valid paths.
- HASS specialist subjects begin at Year 7 (not Year 6 — Year 6 uses /hass/).
