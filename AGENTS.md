# AGENTS.md

This repository contains shared GitHub automation assets. Follow these rules when creating or modifying issue templates, reusable workflows, content templates, or caller workflow examples.

`README.md` is the catalog of which files belong together.
`AGENTS.md` is the development and maintenance policy.

## Scope

Apply these rules to:
- `.github/ISSUE_TEMPLATE/*`
- `.github/templates/*`
- `.github/workflows/*`
- `.github/examples/*`
- `README.md`

## Required Conventions

- Use one English slug per automation family.
- Keep file names aligned by slug.
- Use these file patterns:
- `.github/ISSUE_TEMPLATE/<slug>.md`
- `.github/templates/<slug>.md`
- `.github/workflows/create-<slug>.yml`
- `.github/examples/<slug>-caller.yml`

## Workflow Design Rules

- Reusable workflows must use `workflow_call`.
- Caller workflows must stay thin and only forward inputs from the issue event.
- Standard reusable workflow inputs are:
- `issue_number`
- `issue_title`
- `issue_body`
- `issue_created_at`
- `issue_labels`
- Prefer `actions/github-script` plus GitHub API calls over multi-step shell.
- Do not embed long markdown templates inside shell scripts.
- Store generated markdown structure in `.github/templates/` and replace placeholders in the workflow.

## Naming Rules

- Reusable workflow `name` should follow: `Create <Topic> Assets`
- Caller workflow `name` should follow: `<Topic> Automation`
- Branch naming should be deterministic and documented in the workflow.
- Labels should match the slug when practical.

## Content Template Rules

- Use placeholder tokens such as `{{TITLE}}` and `{{DATE}}`.
- Keep placeholders explicit and uppercase.
- Keep frontmatter keys stable unless there is a documented migration.
- Localized content in markdown templates is allowed.

## Before Adding a New Workflow Family

1. Read `README.md`.
2. Check whether a slug already exists.
3. Reuse the standard workflow inputs.
4. Add the matching issue template, content template, reusable workflow, and caller example.
5. Keep names aligned across all four files.

## Current Reference Family

- Slug: `reading-note`
- Issue template: `.github/ISSUE_TEMPLATE/reading-note.md`
- Content template: `.github/templates/reading-note.md`
- Reusable workflow: `.github/workflows/create-reading-note.yml`
- Caller example: `.github/examples/reading-note-caller.yml`

## Maintenance Preference

- Prefer fewer moving parts.
- Prefer one reusable workflow plus one content template file per family.
- Avoid introducing additional abstraction layers unless there is a clear reuse need.