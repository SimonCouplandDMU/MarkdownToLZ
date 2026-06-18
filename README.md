# Markdown to LearningZone
## A GitHub based Markdown → HTML → SCORM / Common Cartridge Pipeline

## Overview

This repository demonstrates a complete workflow for converting structured Markdown content into:

- Styled HTML pages  
- IMS Common Cartridge packages (for VLE import)  
- SCORM 1.2 packages (legacy LMS compatibility)  

It is designed as a **training and demonstration repository** covering both basic Markdown usage and automated packaging for Learning Zone.  
This is a template repository.  
Click Use this template and you will get your own copy of the repo to play with.

## Disclaimer

I have only tested this with the LearningZone VLE, which is a variant of BrightSpace.
I have tried to keep to standards for both IMS and SCORM, however I cannot guarantee it will work for your VLE.
I recommend you use the next Section to try it our and see if it works with you VLE before proceeding any further.

---

## Try It Out

You can try all the functionality of the repo as is stands.
The folder md has a collection of markdown files.
These can automatically converted to HTML and then package as an IMS Common Cartridge or a SCORM package.
Steps:

1. Browse the folders and files in the **md** folder.  You will notice the are all proceeded with numbers.  These give order the will appear in your VLE.  For number 1 to 9 always put a proceeding 0.
2. Run the **Build HTML from Markdown** action.
3. Pull the repo and browse the files in the HTML file. These are the files that will be packaged.  The numbers in front of the file names are still needed.  I do not recommend edit these files at this point.  If you want changes make them in markdown and rerun the conversion.
4. Package the html files, I recommend you run the **Build Course package** action. Pull again and you will find a file called course-package.zip.  This is the file you need to upload to you VLE.  For Learning Zone you do this with Module Tools &rarr; Course Admin &rarr; Import/Export/Copy Components.  Select Import Components &rarr; from a course package.  Upload course-package.zip and press Import All Components.  Wait a while and you will have a new item in you module shell called **Markdown Course Package** with all the imported content it.

If you're happy with all these steps you can start replacing the markdown files with your own content.  Use folders to give structure and stick to the number convention to ensure your content is presented in your desired order.  The name of each page is taken from the first markdown heading in the file, so you do not need to be precious with file names, just stick to a reasonable convention.  Image file need to be placed in the same folder as the markdown file they are referenced in.  It is a current limitation that if you use an image in multiple markdown files in multiple folder a copy of that image will need to be placed in each folder.

There is more information in the remainder of this read me but you now everything you need to manage and convert you markdown files for importing to Learning Zone.

---

## Repository Structure

### `md/` — Markdown Content

Contains structured course content:

- `01_Markdown Basics/`
  - `01_basic_text.md`
  - `02_links.md`
  - `03_images.md`
- `02_Formatting/`
  - `01_lists.md`
  - `02_tables.md`
  - `03_code.md`
  - `04_blockquotes.md`
  - `05_math.md`
- `03_Nesting_Folders/`
  - Demonstrates deep folder hierarchy and structure-only folders

Images used in content are stored alongside Markdown files.

---

### `.github/workflows/` — Automation

Contains GitHub Actions workflows:

- `buildHTMLusingPandoc.yml`
- `buildCoursePackage.yml`
- `buildSCORMpackage.yml`

---

### `resources/` — Shared Assets

- `github-markdown.css` → base styling
- `custom.css` → additional styles
- `template.html` → Pandoc template

---

### Generated Output

Created during workflows:

- `html/` (temporary build folder)
- `scorm-package.zip`
- `course-package.zip`


---

## Workflows

### 1. Build HTML From Markdown 

> Note: You must run this workflow before building a course or SCORM package.

This workflow converts Markdown into HTML using Pandoc.

**What it does:**

- Converts `.md` → `.html`
- Applies template and CSS styling
- Generates `.title` files for clean navigation names
- Preserves folder structure

⚠️ **This must be run before any packaging workflow.**

---

### 2. Build Common Cartridge Package

Creates an IMS Common Cartridge package.

**What it does:**

- Builds hierarchical course structure from folders
- Uses `.title` files for display names
- Includes all assets (CSS, images)
- Generates CC-compliant `imsmanifest.xml`
- Outputs `.zip` ready for LMS import

✅ Recommended for modern VLEs (e.g. Brightspace Content)

---

### 3. Build SCORM Package

Creates a SCORM 1.2 package.

**What it does:**

- Generates `index.html` launch page
- Builds SCORM-compliant manifest with namespaces and SCOs
- Preserves folder hierarchy
- Includes all assets
- Outputs `scorm-package.zip`

✅ Suitable for legacy LMS or SCORM-only systems

---

## Workflow Order

You must run workflows in this order:

```
1. Build HTML From Markdown
2. Build Common Cartridge OR Build SCORM Package
```

---

## Markdown Features Demonstrated

The repository includes examples of:

- Basic text (bold, italic, strike-through)
- Links (internal and external)
- Images (with alt text)
- Lists (including nested lists)
- Tables (Markdown + HTML)
- Code blocks (Python, Java, C++)
- Blockquotes
- LaTeX maths (via MathJax)

---

## Notes on LaTeX

Inline example:

```
$E = mc^2$
```

Display example:

```
$$
x = rac{-b \pm \sqrt{b^2 - 4ac}}{2a}
$$
```

✅ Supported using MathJax  
❌ Full LaTeX documents are not supported

---

## SCORM vs Common Cartridge

| Feature | Common Cartridge | SCORM |
|--------|------------------|------|
| Modern LMS support | ✅ | ⚠️ |
| Hierarchy | ✅ | ✅ |
| Metadata richness | ✅ | ❌ |
| Launch model | multi-item | single entry (SCO) |

👉 Use **Common Cartridge** where possible.

---

## Best Practices

- Keep Markdown well structured
- Use `.title` files for readable names
- Store images with relevant Markdown
- Do not edit files in `html/`

---

## License

This project is licensed under the MIT License.

---



