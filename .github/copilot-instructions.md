# Copilot Instructions

## Repository direction

The project is a CAD inspection tool, not a renderer-first application.

The first milestone is to understand the STEP structure, inspect entities, and provide a plugin-based extension model.

## Language policy

Use English for:

- documentation
- commit messages
- code comments
- design notes

## Scope policy

Keep work aligned with the current milestone.

Current milestone priorities:

1. STEP import and model parsing
2. entity tree display
3. property inspection
4. plugin architecture
5. targeted visual plugins

Do not expand the scope into a broad renderer or full CAD suite before the structure and inspection flow is working.

## Restricted test data

The JAMA role-model STEP files are local-only test data.

- Store downloaded files only under the ignored `test-data/` directory.
- Never copy, move, rename, modify, publish, distribute, sell, or commit these files.
- Never include the files or derived copies in source code, screenshots, fixtures, archives, build output, or AI prompts.
- Do not upload the files to external services or send them to an AI service.
- Use the files only for local manual verification unless permission is confirmed separately.
- Do not download or relocate the files automatically; ask the user to place them locally when needed.

## Plugin-first rule

When adding functionality, prefer a plugin boundary rather than embedding logic deeply in the application core.

Examples:

- bounding box analysis
- measurement tools
- highlight overlays
- selection utilities
- render adapters

## Issue-based workflow

Work from one GitHub issue at a time. Keep each change small enough for one pull request.

1. **Pick one issue.** Use an issue the user names. If none is named, suggest one and wait for approval. If the issue has no "Done when" list, ask the user to confirm one before starting.
2. **Check the scope.** Confirm the issue fits the current milestone. If it is too big, propose smaller issues instead of starting.
3. **Create a branch from `main`.** Use `feature/<issue-number>-<short-name>`, `fix/<issue-number>-<short-name>`, or `docs/<issue-number>-<short-name>`. Never commit directly to `main`.
4. **Make only the requested change.** Do not fix unrelated problems. Record them as new issue suggestions instead.
5. **Check the work.** Run `npm run typecheck`, `npm run lint`, `npm test`, and `npm run build`. Report any check that was skipped or failed.
6. **Commit in English.** Use a short, clear message. Reference the issue, for example `Add entity search (#12)`.
7. **Open a pull request.** Fill in the pull request template. Use `Closes #<issue-number>` so the issue closes when merged. Do not merge it yourself unless the user asks.
8. **Update the notes.** If `docs/TODO.md` lists the work, tick it or link the issue. Do not duplicate details that live in the issue.

### Writing new issues

Use the matching template in `.github/ISSUE_TEMPLATE/` (Task, Feature, or Bug). Every issue needs a clear goal and a short "Done when" checklist. Keep one outcome per issue. Prefer a task that takes less than a day.

### Recording decisions

When a decision is hard to reverse, write a short note in `docs/adr/` named `NNNN-short-title.md`, and link it from the issue or pull request. Examples: choosing the OCCT binding, the node export format, or the input binding model.

### Safety reminders

- Never put confidential or restricted data in issues, pull requests, commits, or prompts. This includes CAD/STEP models, other binary files, screenshots, logs, credentials, personal data, and anything derived from them.
- Do not add binary files to the repository unless the issue asks for them and the user approves.
- If you are unsure whether something is confidential, leave it out and ask the user.
- Never create, edit, or close issues, labels, or settings in bulk without the user's approval.
- Do not run destructive git commands such as force push or hard reset unless the user asks.

## Write clearly

Prefer short, readable explanations and simple English language.
