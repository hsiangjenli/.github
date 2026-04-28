# .github Automation Catalog

This README is the catalog for shared GitHub assets in this repository.

Use it to answer:
- Which issue template belongs to which reusable workflow
- Which markdown template that workflow uses
- Which caller example a target repository should copy

Development rules live in `AGENTS.md`.

## Asset Locations

- Issue templates: `.github/ISSUE_TEMPLATE/`
- Reusable workflows: `.github/workflows/`
- Markdown templates: `.github/templates/`
- Caller examples: `.github/examples/`

## Workflow Families

| Slug | Issue Template | Reusable Workflow | Markdown Template | Caller Example | Notes |
|------|----------------|-------------------|-------------------|----------------|-------|
| `reading-note` | `.github/ISSUE_TEMPLATE/reading-note.md` | `.github/workflows/create-reading-note.yml` | `.github/templates/reading-note.md` | `.github/examples/reading-note-caller.yml` | Creates `source/_posts/note_{isbn}.md` in the target repo and runs when the issue has the `reflection` label |

## Standalone Templates

These files do not currently belong to an issue-driven automation family:

| File | Purpose |
|------|---------|
| `.github/ISSUE_TEMPLATE/bug_report.md` | Standard bug report template |

## Reading Note Flow

1. Create an issue from `.github/ISSUE_TEMPLATE/reading-note.md`.
2. Add or keep the `reflection` label on the issue.
3. In the target repository, use `.github/examples/reading-note-caller.yml` as `.github/workflows/reading-note.yml`.
4. The caller triggers `.github/workflows/create-reading-note.yml`.
5. The reusable workflow reads `.github/templates/reading-note.md` and generates `source/_posts/note_{isbn}.md`.
6. Open a PR with `Closes #<issue_number>` to link and close the issue.

## Filename Check

The current `reading-note` family is aligned by slug:
- `.github/ISSUE_TEMPLATE/reading-note.md`
- `.github/workflows/create-reading-note.yml`
- `.github/templates/reading-note.md`
- `.github/examples/reading-note-caller.yml`

If a new workflow family is added, document the same four-file mapping here.