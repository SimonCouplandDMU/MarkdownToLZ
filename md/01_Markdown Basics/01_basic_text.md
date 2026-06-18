## Basic Text

Markdown lets you write formatted text easily.

---

### Emphasis

**Bold text**  
*Italic text*  
***Bold and italic***

---

### Strikethrough

~~This text is crossed out~~

(Note: Supported in most Markdown variants, including Pandoc)

---

### Superscript and Subscript

Markdown does not natively support superscript/subscript,  
but you can use inline HTML:

H<sub>2</sub>O (subscript)  
E = mc<sup>2</sup> (superscript)

---

### Paragraphs and Line Breaks

This is one paragraph.

This is another paragraph.

To force a line break, add two spaces at the end of a line.  
This line appears directly below the previous one.

---

### Escaping Characters

Use a backslash to escape special characters:

\*This is not italic\*  
\# This is not a heading

---

### Horizontal Rule

You can add a horizontal rule:

---

---

### Mixing Formatting

You can combine styles:

**Bold**, *italic*, and ~~strikethrough~~ together.

---

### Notes

- Markdown is designed to be simple and readable
- Some features (like subscript/superscript) rely on HTML
- This conversion pipeline (Pandoc + HTML) supports these
