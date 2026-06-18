# Markdown → HTML → SCORM / Common Cartridge Pipeline

## Overview

This repository demonstrates a complete workflow for converting structured Markdown content into:

- ✅ Styled HTML pages  
- ✅ IMS Common Cartridge packages (for VLE import)  
- ✅ SCORM 1.2 packages (legacy LMS compatibility)  

It is designed as a **training and demonstration repository** covering both Markdown usage and automated LMS packaging.

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
- `cc-package.zip`

⚠️ These files are generated and should not be edited manually.

---

## Workflows

### 1. Build HTML From Markdown ✅ REQUIRED FIRST

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

## Summary

This repository provides a complete pipeline to:

✅ Author content in Markdown  
✅ Convert to HTML  
✅ Package for LMS delivery  
✅ Support both modern (CC) and legacy (SCORM)

