# ENEL445 Power Systems Optimisation Study Pack

This repository is a study pack for the ENEL445 Applied Engineering Optimisation topic on **Power Systems Optimisation**. It is written for learners who are new to power systems but need to understand the optimisation ideas well enough for revision, exam answers, and cheat-sheet preparation.

The material is based on lecture slides, tutorial/practice questions, exam-style questions, and lecture transcripts for the two power systems lectures.

## Quick Start

If you are new to this topic, read the files in this order:

1. `final_notes/appendix_power_systems_ee_background.pdf`
   - Start here if you are not confident with electrical engineering background.
   - Covers active/reactive power, per unit, admittance, susceptance, LFH/PowerFactory, and state-estimation background.

2. `final_notes/power_systems_optimisation_learning_guide.pdf`
   - Main study guide.
   - Covers economic dispatch, penalty factors, OPF, DC OPF, SC-OPF, state estimation, least squares, KKT/convexity links, and exam templates.

3. `final_notes/power_systems_optimisation_exam_cheatsheet.pdf`
   - Compact 2-page English cheat sheet.
   - Use this for final exam preparation and quick recall.

4. `final_notes/appendix_linear_affine_basics.pdf`
   - Read this if you are rusty on linear maps, affine constraints, offset terms, convex optimisation, or KKT notation.

## Repository Structure

```text
.
├── README.md
├── terminology.json
├── transcription_prompt.md
├── transcribe_A.md
├── transcribe_B.md
├── code/
│   └── economic_dispatch_example_solution.ipynb
├── final_notes/
│   ├── power_systems_optimisation_learning_guide.qmd
│   ├── power_systems_optimisation_learning_guide.pdf
│   ├── power_systems_optimisation_exam_cheatsheet.qmd
│   ├── power_systems_optimisation_exam_cheatsheet.pdf
│   ├── appendix_power_systems_ee_background.qmd
│   ├── appendix_power_systems_ee_background.pdf
│   ├── appendix_linear_affine_basics.qmd
│   └── appendix_linear_affine_basics.pdf
├── media/              # ignored: raw lecture audio/video
└── source_materials/   # ignored: raw lecture/exam PDFs
```

## What Each File Is For

| File | Purpose |
|---|---|
| `terminology.json` | English-to-Chinese terminology map for this topic. |
| `transcription_prompt.md` | Prompt for Whisper/transcription API to improve technical term recognition. |
| `transcribe_A.md` | Transcript for Lecture A. |
| `transcribe_B.md` | Transcript for Lecture B. |
| `final_notes/power_systems_optimisation_learning_guide.qmd` | Source for the detailed study guide. |
| `final_notes/power_systems_optimisation_learning_guide.pdf` | Rendered detailed study guide. |
| `final_notes/power_systems_optimisation_exam_cheatsheet.qmd` | Source for the compact English cheat sheet. |
| `final_notes/power_systems_optimisation_exam_cheatsheet.pdf` | Rendered 2-page cheat sheet. |
| `final_notes/appendix_power_systems_ee_background.qmd` | Source for EE background appendix. |
| `final_notes/appendix_power_systems_ee_background.pdf` | Rendered EE background appendix. |
| `final_notes/appendix_linear_affine_basics.qmd` | Source for linear/affine/KKT basics appendix. |
| `final_notes/appendix_linear_affine_basics.pdf` | Rendered linear/affine/KKT basics appendix. |
| `code/economic_dispatch_example_solution.ipynb` | Small notebook for economic dispatch calculation practice. |

## Main Concepts

You should be able to explain and use:

- Economic dispatch: minimise generation cost while meeting demand.
- Incremental cost: $IC_i=dC_i/dP_{G_i}$.
- Penalty factor: adjusts marginal cost for transmission losses.
- Uniform pricing vs pay-as-bid.
- AC OPF: accurate but large, nonlinear, and non-convex.
- DC OPF: linear approximation used for fast dispatch.
- SC-OPF: dispatch with contingency/security constraints.
- State estimation: least-squares estimate of power-system states from noisy measurements.
- Reference bus/angle: needed because voltage angles are relative.
- Weighted least squares: $R=\mathrm{diag}(\sigma_i^2)$.
- Convex vs non-convex optimisation and what KKT conditions mean.

## Exam-Focused Advice

For a short exam answer, prioritise:

1. Clear definitions.
2. Correct notation.
3. Standard formulations.
4. One or two precise reasons, not long prose.

The most useful templates are in:

- `final_notes/power_systems_optimisation_exam_cheatsheet.pdf`
- `final_notes/power_systems_optimisation_learning_guide.pdf`, especially the `Exam Templates` section.

Common traps:

- Do not confuse `DC OPF` with a DC electrical grid. It is a DC approximation of AC power flow.
- Do not forget the reference angle in state estimation.
- Do not solve a least-squares problem if the exam only asks you to formulate it.
- Do not say AC OPF is hard only because it is large; mention nonlinear, non-convex, many constraints, and real-time limits.
- Do not treat an AC power-flow feasibility check as the same thing as solving AC OPF.

## Regenerating PDFs

The `.qmd` files are Quarto source files. To regenerate a PDF:

```bash
quarto render final_notes/power_systems_optimisation_learning_guide.qmd
quarto render final_notes/power_systems_optimisation_exam_cheatsheet.qmd
quarto render final_notes/appendix_power_systems_ee_background.qmd
quarto render final_notes/appendix_linear_affine_basics.qmd
```

The Chinese notes use XeLaTeX through Quarto.

## Git Ignore Policy

This repo is intended to upload **study deliverables**, not raw media.

Ignored:

- raw lecture audio/video in `media/`;
- raw lecture/exam PDFs in `source_materials/`;
- `.DS_Store`;
- Quarto/LaTeX intermediate files;
- large accidental root-level media/PDF files.

Tracked deliverables should include:

- `final_notes/*.qmd`;
- `final_notes/*.pdf`;
- transcripts;
- terminology and transcription prompt;
- small code examples.

