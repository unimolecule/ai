# Language README Rules

This project README skill provides lightweight localization support. If the user's primary task is translating an existing README, preserving Markdown structure across languages, adding language selectors, or maintaining localized variants, prefer a dedicated README i18n skill when available.

## Primary Rules

- `README.md` is always English.
- Do not create localized README files by default when the user asks in English and does not request another language.
- If the user explicitly requests Chinese, French, Japanese, or another language, also create that language README.
- If the user does not explicitly request localization but the conversation language is not English, create `README.md` in English and one localized README in the user's conversation language.
- Keep localized files aligned with the English README in structure, links, command examples, warnings, and factual content.
- Preserve code blocks, commands, env var names, package names, badge URLs, image URLs, and relative links unless the user explicitly asks to localize them.

## Language Links

- Add language links directly under badges and before warnings or overview prose.
- English is always the first item in the language switcher.
- Chinese is always second when present.
- Additional languages follow after English and Chinese in the order requested by the user.
- On `README.md`, make English bold and link localized files.
- On localized files, keep English first as a link, make the current language bold, and link other localized files.

Use these common filenames and labels unless the repo already has a different convention:

| Language            | Filename          | Label                 |
| ------------------- | ----------------- | --------------------- |
| English             | `README.md`       | `English`             |
| Simplified Chinese  | `README.zh-CN.md` | `Chinese`             |
| Traditional Chinese | `README.zh-TW.md` | `Traditional Chinese` |
| French              | `README.fr.md`    | `French`              |
| Japanese            | `README.ja.md`    | `Japanese`            |
| Korean              | `README.ko.md`    | `Korean`              |
| Spanish             | `README.es.md`    | `Spanish`             |
| German              | `README.de.md`    | `German`              |

English README example:

```html
<p><strong>English</strong> | <a href="./README.zh-CN.md">Chinese</a></p>
```

Chinese README example:

```html
<p><a href="./README.md">English</a> | <strong>Chinese</strong></p>
```

English + Chinese + French example on English README:

```html
<p>
  <strong>English</strong> | <a href="./README.zh-CN.md">Chinese</a> |
  <a href="./README.fr.md">French</a>
</p>
```
