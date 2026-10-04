# ResumeFit

A single-file web app that reformats a resume into the look of a Word template.

**Run it:** use the live version at https://morganisms.github.io/resumefit/, or download `index.html` and open it in any modern browser. There's no install and no server.

## How it works

1. **Add a template**: a `.docx` or `.dotx` file in the style you want.
2. **Add a resume**: a `.pdf`, `.docx` or `.txt` file, or paste the text.
3. **Check the content**: ResumeFit splits the resume into name, contact details and sections. Fix anything that landed in the wrong place; the preview updates as you type.
4. **Download**: you get a new `.docx` with the resume's content in the template's fonts, sizes, colors, spacing, borders, bullets, page size, margins, headers and footers.

## Features

- **Two kinds of template**:
  - *Sample content* (default): any resume already formatted the way you want. ResumeFit finds one example of each element (name, contact line, section heading, role or school line, second line, paragraph, bullet), copies its formatting and rebuilds the document with the new content.
  - *Placeholders*: a template containing `{{tags}}`. The template's own layout is kept, including tables, and each tag is filled in place. See the tag list below.
- **Formats found**: the Template panel lists each element it found in the template. Anything missing is built from the template's paragraph style.
- **Right-aligned dates**: dates at the end of a role or school line (for example `Director | Jan 2021 – Present`) go on a right tab stop, using the template's date formatting when it has one.
- **Editable content**: rename, reorder, add or remove sections before downloading.
- **Starter template**: download a ready-made template to try the tool or use as a base for your own.
- **Light and dark mode**: follows your system setting until you choose one with the toggle in the header.

## Content syntax

Each section in *Check the content* is plain text, one item per line:

| Line starts with | Becomes | Example |
|---|---|---|
| `## ` | Role or school line (dates at the end are right-aligned) | `## Senior Program Manager \| Mar 2016 – Dec 2020` |
| `### ` | Second line, such as company and location | `### Helix Instruments, Emeryville, CA` |
| `- ` | Bullet | `- Took the platform to 510(k) clearance` |
| anything else | Paragraph | `Portfolio management, stage-gate governance` |

## Placeholder tags

Tags are case-insensitive and can sit in the body, header or footer.

| Tag | Fills with |
|---|---|
| `{{name}}` | Name |
| `{{contact}}` | All contact details on one line |
| `{{email}}`, `{{phone}}`, `{{location}}`, `{{linkedin}}`, `{{website}}` | One contact detail each |
| `{{summary}}`, `{{experience}}`, `{{education}}`, `{{skills}}`, `{{certifications}}`, `{{publications}}`, `{{projects}}`, `{{awards}}`, `{{volunteer}}`, `{{languages}}`, `{{interests}}` | That section's content, without its heading (put your own heading above the tag) |
| `{{section: Any Title}}` | The section with that exact title |
| `{{sections}}` | Every section not used by another tag, each with its heading |

A section tag works best alone in its own paragraph: that paragraph's formatting is used for the section's body text. Tags in a line with other text are filled inline.

## Tips and limits

- Text-based PDFs work best. Scanned PDFs have no text to read; use the Word version or paste the text.
- Multi-column PDF layouts can come through out of order. Check the content step before downloading.
- With a *sample content* template, the output is a single column. To keep a table-based layout, use placeholders.
- Older `.doc` files aren't supported. Save them as `.docx` first.
- Open the result in Word to check page breaks before sending it.

## Data

Files are read and built entirely in your browser; nothing is uploaded or stored. Only the light/dark choice is saved, in local storage. The Word and PDF readers (JSZip and PDF.js) load from cdnjs, which needs an internet connection; pasted text works without them.
