---
name: tech-solution-ppt
description: Create leadership-facing technical solution PPTs using the saved HKUST(GZ) template and a problem-to-solution narrative.
metadata:
  short-description: 技术解决方案汇报PPT模板与方法论
---

# Technical Solution PPT

Use this skill when the user asks for a technical solution, project plan, customer-response deck, leadership report, or engineering proposal PPT and wants the same style and logic as the G1 softball throw/catch deck.

## Saved Template

Use `assets/hkust-gz-technical-template.pptx` as the preferred visual template unless the user provides a newer template. Treat the template as a design source, not a content source:

- Preserve the white background, deep-blue top bar, HKUST(GZ)-style academic/technical tone, restrained colors, and clean engineering layout.
- Delete irrelevant old slide content.
- Reuse the template's slide dimensions, fonts, title rhythm, footer behavior, and simple boxed structure.
- Keep output as editable `.pptx`; use native PowerPoint tables and editable labels where possible.

## Required Reading

Before creating or revising a deck with this skill, read `references/methodology.md`.

Also use the built-in `presentations` skill for PPT implementation, rendering, validation, and delivery.

## Working Style

Default to making the deck, not only proposing an outline, when the user has provided enough draft content.

For leadership-facing technical plans:

- Start from the customer's domain and task reality, then derive requirements.
- Show the logic diagram before dense explanation.
- Explain why each module exists by tying it to a domain constraint or customer question.
- Avoid opening with "leadership concerns" as a list; make those concerns emerge naturally from the problem and solution.
- Use diagrams, concept visuals, and flowcharts generously, but keep captions and labels short.
- Make timelines concrete: each milestone should have a date, goal, work items, deliverables, and acceptance evidence.
- End with decision points only when leadership action is needed.

When useful, generate or reuse visual concept images, but keep important explanations as editable PPT text layered on top or beside the image.
