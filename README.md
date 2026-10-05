# ResumeFit

A single-file web app that reformats a resume into the look of a Word template.

**Run it:** use the live version at https://morganisms.github.io/resumefit/, or download `index.html` and open it in any modern browser. There's no install and no server.

## How it works

1. **Add a template**: a `.docx` or `.dotx` file in the style you want.
2. **Add a resume**: a `.pdf`, `.docx` or `.txt` file, or paste the text.
3. **Check the content**: ResumeFit splits the resume into name, headline or credentials, contact details and sections. Fix anything that landed in the wrong place; the preview updates as you type.
4. **Download**: you get a new `.docx` built from the template itself. Its layout, sidebars, pictures, fonts, colors, spacing, bullets, headers and footers stay as they are, and its sample text is replaced with the resume's content.

## Features

- **Two kinds of template**:
  - *Layout* (default): a blank company template with sample text ("Full Name", "Company Name • City, ST", "Job Title", "University Name") or any resume already formatted the way you want. ResumeFit reads the template's layout, including sidebars and text boxes, and fills each part in place.
  - *Placeholders*: a template containing `{{tags}}`. Each tag is filled in place. See the tag list below.
- **Section matching**: each template section is filled from the resume section on the same topic, so a resume's *Skills* fills a template's *Core Competencies* and *Education* lands in a sidebar if that's where the template puts it. The Template panel shows what goes where, which template sections will be removed because the resume has nothing for them, and which resume sections are added at the end of the main column.
- **Entry formats**: ResumeFit learns how the template lays out each entry (for example company and location on one line, then job title with dates on the right) and rebuilds every job, degree and certification in that order and format.
- **Contact details**: email, phone, LinkedIn and location fill the template's contact slots, sidebar or header line. A template's LinkedIn link is pointed at the real profile.
- **Headers**: sample names and credentials in page headers are replaced too.
- **Sidebar resumes**: two-column PDF resumes are read column by column, so sidebar details don't get mixed into the main text.
- **Editable content**: rename, reorder, add or remove sections before downloading.
- **Starter template**: download a ready-made template to try the tool or use as a base for your own.
- **Light and dark mode**: follows your system setting until you choose one with the toggle in the header.

## Content syntax

Each section in *Check the content* is plain text, one item per line:

| Line starts with | Becomes | Example |
|---|---|---|
| `## ` | Entry heading: role, degree or certification, with dates at the end | `## Senior Program Manager \| Mar 2016 – Dec 2020` |
| `### ` | Second entry line, such as company and location | `### Helix Instruments, Emeryville, CA` |
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
- Letter-spaced text in PDFs (common in headings) is rejoined for standard section names; other letter-spaced lines may need a quick fix in the content step.
- A sidebar is a fixed-size box in Word. If the resume has more sidebar content than the template allows for, shorten it in the content step or resize the box in Word.
- Section matching works by topic. To send a section somewhere else, rename it in the content step to match the template's section title.
- Older `.doc` files aren't supported. Save them as `.docx` first.
- Open the result in Word to check page breaks before sending it.

## Data

Files are read and built entirely in your browser; nothing is uploaded or stored. Only the light/dark choice is saved, in local storage. The Word and PDF readers (JSZip and PDF.js) load from cdnjs, which needs an internet connection; pasted text works without them.
