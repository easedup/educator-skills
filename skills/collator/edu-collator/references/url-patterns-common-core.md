# EasedUP URL Patterns — Common Core State Standards

Base URL: `https://common-core.easedup.com`
MCP URL:  `https://common-core.easedup.com/mcp`

Append `.md` to any curriculum page path to get the clean Markdown version.
Always fetch the `.md` version, not the HTML page.

---

## English Language Arts & Literacy (K–5)
```
/ela-literacy/kindergarten.md
/ela-literacy/grade-1.md
/ela-literacy/grade-2.md
/ela-literacy/grade-3.md
/ela-literacy/grade-4.md
/ela-literacy/grade-5.md
```

## English Language Arts (6–12)
```
/ela/grade-6.md
/ela/grade-7.md
/ela/grade-8.md
/ela/grade-9-and-10.md
/ela/grade-11-and-12.md
```

## Literacy in History/Social Studies, Science & Technical Subjects (6–12)
```
/literacy/grade-6-to-8.md
/literacy/grade-9-and-10.md
/literacy/grade-11-and-12.md
```

## Mathematics (K–8)
```
/mathematics/kindergarten.md
/mathematics/grade-1.md
/mathematics/grade-2.md
/mathematics/grade-3.md
/mathematics/grade-4.md
/mathematics/grade-5.md
/mathematics/grade-6.md
/mathematics/grade-7.md
/mathematics/grade-8.md
```

## Mathematics (High School — by domain)
```
/mathematics/high-school-number-and-quantity.md
/mathematics/high-school-algebra.md
/mathematics/high-school-functions.md
/mathematics/high-school-geometry.md
/mathematics/high-school-statistics-and-probability.md
```

---

## Notes

- The `.md` files include a `queried:` timestamp in the frontmatter — cite this
  when referencing standards so teachers know how current the content is.
- ELA splits at Grade 6: use `/ela-literacy/` for K–5, `/ela/` for 6–12.
- High school Mathematics is organised by domain, not grade — fetch the relevant
  domain file/s for the content area being taught.
- If a URL returns 404, use the MCP `get_all` tool or check
  `https://common-core.easedup.com` for valid paths.
- Common Core does not cover Science or Social Studies — for those subjects,
  check state-specific standards.
