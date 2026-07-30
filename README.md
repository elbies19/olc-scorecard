# OLC Course Review Scorecard — Self-Assessment Tool

A browser-based self-assessment tool for faculty and instructional designers, built on the [OLC Center for Quality Initiatives Course Review Scorecard](https://onlinelearningconsortium.org/quality/scorecards/course-review/). Designed for developmental, formative self-assessment rather than formal peer review or OLC Exemplary Endorsement.

**Live tool:** [elbies19.github.io/olc-scorecard](https://elbies19.github.io/olc-scorecard/)

---

## Background

The OLC Course Review Scorecard is a free, open-access instrument for evaluating the design, delivery, and overall effectiveness of online and blended courses. It consists of 50 measurable objectives across three sections:

- **Essential Design** (20 objectives, 40 points) — foundational course components
- **Advanced Design** (15 objectives, 30 points) — higher-level instructional strategies
- **Course Delivery** (15 objectives, 30 points) — instructor facilitation and presence

While OLC offers a [custom GPT-based assistant](https://onlinelearningconsortium.org/publications-resources/quality-resources/) for working through the scorecard, usage limits on the free tier of ChatGPT can interrupt the review process mid-session. This tool provides an alternative built on Anthropic's API, with no turn limits, no account required, and no session interruptions.

---

## Features

- **Full OLC scorecard implementation** — all 50 objectives across all three sections, scored 0–2 per the official Developing / Accomplished / Exemplary scale
- **Inline criteria guidance** — each objective includes an ⓘ button showing the detailed 0/1/2 criteria from the [OLC Course Review Handbook](https://onlinelearningconsortium.org/publications-resources/quality-resources/)
- **Document upload and analysis** — upload a syllabus addendum, modules list, or other course document (PDF or .txt); the tool extracts evidence notes and suggests scores for relevant objectives using Claude Sonnet via a secured Cloudflare Worker
- **Evidence notes** — each objective includes an optional evidence/notes field for documenting what in the course informed the rating, consistent with OLC's evidence-based scoring approach
- **AI-assisted narrative drafting** — once sufficient evidence notes are added, draft buttons generate Strengths and Areas for Improvement narratives grounded in the actual evidence provided
- **Point-in-time Course Delivery review** — Course Delivery can be completed after a course, or mid-semester as a formative point-in-time review
- **Print / Save as PDF** — generates a complete self-assessment report including section narratives, an improvement plan, and a full objective-by-objective breakdown with scores and evidence notes
- **WCAG 2.1 AA accessible** — keyboard navigable, screen reader compatible, visible focus indicators, sufficient color contrast throughout

---

## OLC Resources

| Resource | Link |
|---|---|
| Course Review Scorecard (download) | [onlinelearningconsortium.org/quality/scorecards/course-review](https://onlinelearningconsortium.org/quality/scorecards/course-review/) |
| Course Review Handbook | [OLC Quality Resources](https://onlinelearningconsortium.org/publications-resources/quality-resources/) |
| Course Review Scorecard FAQ | [OLC Quality Resources](https://onlinelearningconsortium.org/publications-resources/quality-resources/) |
| OLC Course Review Services | [onlinelearningconsortium.org/quality/review-services/course-reviews](https://onlinelearningconsortium.org/quality/review-services/course-reviews/) |
| All OLC Quality Scorecards | [onlinelearningconsortium.org/quality/scorecards](https://onlinelearningconsortium.org/quality/scorecards/) |

---

## Appropriate Use and Data Handling

This tool is designed to evaluate **course design and delivery — not student performance.**

**Do not upload** documents containing student data, including gradebooks, assignment submissions, student emails, or any materials that identify individual students. Uploading such materials may constitute a FERPA violation.

**Appropriate documents to upload** include syllabi, course schedules, module outlines, assignment descriptions, and instructor-created course materials.

**Data handling:**
- Scorecard scores and written narratives are stored in the browser only and are cleared when the tab is closed
- Documents and text submitted for AI-assisted features are transmitted to Anthropic's API for processing via a secured Cloudflare Worker
- Anthropic does not use API calls to train its models by default — no opt-out required
- Uploaded documents are processed and returned; they are not stored by this tool
- For questions about data handling, appropriate use, or FERPA compliance, contact your supervisor or the Academic Technology office before proceeding

See [Anthropic's Privacy Policy](https://privacy.anthropic.com) for details on API data handling.

---

## Technical Stack

- Single-file HTML — no build step, no dependencies to install
- React 18 + Babel (in-browser transpilation) via CDN
- [Cloudflare Worker](https://workers.cloudflare.com/) — thin API proxy that holds the Anthropic API key server-side; does not store or log request content
- Anthropic API — Claude Haiku for narrative drafting, Claude Sonnet for document analysis

---

## Scoring Scale

| Score | Label | Description |
|---|---|---|
| 0 | Developing | Does not yet meet the baseline standard. Requires improvement. |
| 1 | Accomplished | Meets minimum expectations for quality and effectiveness. |
| 2 | Exemplary | Surpasses standard expectations; demonstrates highly effective practice. |

---

## License and Attribution

The OLC Course Review Scorecard is published by the [Online Learning Consortium](https://onlinelearningconsortium.org) under [CC BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/). This tool is built on and references that scorecard and its associated handbook and FAQ materials. It is intended for institutional and educational use only and is not affiliated with or endorsed by OLC.

---

*Built by Lauren B. Schwartz, Instructional Development Specialist, Salem Community College*  
*Part of the [SCC Academic Technology toolkit](https://elbies19.github.io)*
