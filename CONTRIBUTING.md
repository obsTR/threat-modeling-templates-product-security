# Contributing Guide

Thanks for contributing to `threat-modeling-templates-product-security`.

## Ways to Contribute
- Add a new STRIDE or PASTA template variant.
- Add a realistic example under `examples/`.
- Improve wording, consistency, or structure in existing templates.
- Report bugs and request features via GitHub Issues.

## Repository Conventions
- Keep templates and examples in Markdown (`.md`).
- Use clear section headers and table-based risk/threat entries.
- Prefer practical mitigations and actionable requirement statements.
- Use ticket IDs in examples where useful (e.g., `SEC-101`).

## Adding a New Example
1. Copy from `templates/STRIDE_assessment.md` or `templates/PASTA_risk_analysis.md`.
2. Save the new file under `examples/` with a descriptive name.
3. Populate all sections with concrete, realistic content.
4. Update `README.md` under `## Examples` with your new file link.

## Pull Request Checklist
- [ ] Content is accurate and free of placeholders (unless intentional template placeholders).
- [ ] Markdown renders correctly on GitHub.
- [ ] `README.md` is updated when adding new templates/examples.
- [ ] Naming follows existing pattern (`*_stride.md`, `*_pasta.md`).

## Code of Conduct
Be respectful, constructive, and specific in review feedback.
