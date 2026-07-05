# Writing Reference Guide

A quick reference for writing clear, maintainable, and professional documentation.

---

# General Principles

- Write for humans first.
- Be concise.
- Use active voice whenever possible.
- Prefer simple words over complex ones.
- Keep paragraphs short.
- Explain *why*, not just *what*.
- Use consistent terminology.

Example:

The operation will be performed by the service.

The service performs the operation.

---

# Document Structure

```text
Title

Overview

Prerequisites

Architecture / Background

Implementation

Examples

Edge Cases

Best Practices

Troubleshooting

References
```

---

# Markdown Headings

```md
# H1 - Title

## H2 - Section

### H3 - Subsection

#### H4 - Small subsection
```

Use only one `#` heading per document.

---

# Paragraphs

Keep paragraphs between 2–5 sentences.

---

# Lists

## Unordered

```md
- Item
- Item
  - Nested Item
```

## Ordered

```md
1. Step one
2. Step two
3. Step three
```

---

# Tables

```md
| Name | Description |
|------|-------------|
| API | Application Programming Interface |
| DB | Database |
```

---

# Code Blocks

Specify the language.

````md
```python
print("Hello")
```

```javascript
console.log("Hello");
```

```json
{
  "name": "example"
}
```

---

# Inline Code
Use backticks.

```md
Use `docker build`.
```

---

# Quotes

```md
> Important note.
```
---

# Callouts

> **Note**
> Useful information.

> **Warning**
> Be careful.

> **Tip**
> Helpful suggestion.

---

# Links

[OpenAI](https://openai.com)

---

# Images

![Architecture](images/architecture.png)

---

# Task Lists

- [ ] Todo
- [x] Completed

---

# Horizontal Rule

---
---

# Emphasis

*italic*

**bold**

***bold italic***

~~strikethrough~~

---

# File Tree

project/
├── docs/
│   ├── api.md
│   └── architecture.md
├── src/
└── README.md