# PE Assessment Portal

A single-file, browser-based assessment and report card system built for school Physical Education departments. Teachers record skill-based marks for their classes, and administrators manage the roster, domains, and report card generation — all from one HTML file backed by a [Supabase](https://supabase.com) database.

## Overview

The portal is built around a competency-based assessment model rather than simple marks out of 100. Students are evaluated against **Learning Outcomes** grouped into **Subskills**, which in turn sit under broader **Domains** (e.g. Physical Development, Social-Emotional Development, Cognitive Development). Each outcome is graded using a configurable 5-level scale (Foundation → Role Model by default), and the system rolls these up into subskill, domain, and overall student levels — culminating in a printable report card.

Everything runs client-side as plain HTML/CSS/JavaScript with no build step or server required. Data is persisted to a Supabase (PostgreSQL) backend over its REST API.

## Key Features

### Teacher workflow
- Login with a teacher account scoped to specific class/section assignments.
- A guided, stepper-based flow: select term → domain → subskill → section, then enter outcome-level grades for every student.
- Draft saving and a formal "Submit" step that locks a section's marks.
- Per-section Excel (CSV) and PDF export of entered marks.
- Dashboard showing submitted vs. pending sections at a glance.

### Admin (Super Admin) workflow
- **Dashboard** — school-wide submission stats and principal signature management.
- **User Management** — add/edit/deactivate teacher accounts, assign roles, and upload digital signatures.
- **Student Records** — add, import (via Excel/CSV), edit, and bulk-manage the student roster, including admission number, DOB, and parent details where the schema supports it.
- **Subskills & Outcomes** — define domains and subskills, attach 6–10 learning outcomes to each subskill, and filter/preview them in a snapshot view.
- **Assessment Levels** — customize the 5-tier grading scale (labels, descriptions, colors) or reset to the default L1–L5 scheme.
- **Assign Classes** — map teachers to the class-sections they're responsible for.
- **Classes & Sections** — configure which sections exist for each grade/class.
- **Report Cards** — search/filter students, preview an individual report card, and print or save-to-PDF either a single student or an entire section/class, for Term 1, Term 2, or a consolidated full-year report.
- **Master Reset** — a guarded, type-to-confirm tool to wipe selected data tables from both the session and the Supabase database (intended for end-of-year resets or fresh deployments).

### Report cards
Generated report cards include the school header, student information, the scoring rubric/legend, a signature block, and a per-domain breakdown of subskills and learning-outcome levels — formatted for printing on school letterhead.

## Tech Stack

- **Frontend**: Vanilla HTML, CSS, and JavaScript (no framework, no build tools)
- **Backend**: [Supabase](https://supabase.com) (PostgreSQL + auto-generated REST API)
- **Fonts**: Google Fonts (Playfair Display, IBM Plex Sans)
- **Excel import/export**: [SheetJS (xlsx)](https://github.com/SheetJS/sheetjs), loaded dynamically on first use
- **PDF/print**: Browser-native print dialog (`window.print()`) against a print-formatted HTML view

