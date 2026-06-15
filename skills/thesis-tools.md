---
name: thesis-tools
description: Graduation thesis writing, formatting, and code-to-documentation conversion. Use when writing thesis chapters, generating docs from code, manipulating Word files with Python, or preparing defense materials.
---

# Thesis Tools

Comprehensive assistant for academic thesis work, especially for CS/engineering graduation projects.

## Thesis Writing

### Standard CS Thesis Structure
1. Abstract (CN + EN) — purpose, method, results, conclusion (300-500 words)
2. Chapter 1: Introduction — background, literature review, significance
3. Chapter 2: Related Technologies — tech stack overview with rationale
4. Chapter 3: Requirements Analysis — functional/non-functional, use cases
5. Chapter 4: System Design — architecture, database, API, modules
6. Chapter 5: System Implementation — core features, key code, screenshots
7. Chapter 6: System Testing — test cases, results, performance
8. Chapter 7: Conclusion — summary, limitations, future work
9. References
10. Acknowledgments

### Language Standards
- Third-person, objective tone (no "I", "we")
- Passive voice for technical descriptions
- Define terms on first use
- Figures: "Figure X-X" with captions below
- Tables: "Table X-X" with captions above
- Citations: [1], [2-5]

### Common Phrases
- "This thesis designs and implements..."
- "To address the problem of..."
- "Experimental results show that..."
- "As illustrated in Figure X-X..."
- "Table X-X presents..."

## Code → Documentation

Generate thesis content directly from source code:
- **From Controllers** → API documentation table (endpoint, method, params, description)
- **From Entities/SQL** → Database table descriptions, ER diagrams
- **From Solidity** → Smart contract function docs
- **From Service classes** → Business logic flow descriptions

## Word Document Automation

### Environment
```bash
pip install python-docx
```

### Read
```python
from docx import Document
doc = Document('thesis.docx')
for para in doc.paragraphs:
    print(para.text)
```

### Replace text (preserving format)
```python
for para in doc.paragraphs:
    if 'old' in para.text:
        for run in para.runs:
            run.text = run.text.replace('old', 'new')
doc.save('output.docx')
```

### Notes
- `.doc` files must be converted to `.docx` first
- Always backup before batch modifications
- Complex tables may need special handling
