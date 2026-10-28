# Conflict Notes

## What happened
Both `main` and `proposal` modified the same line of `README.md`
(the `Status:` line) after the `proposal` branch was created.

| Branch | Version of the line |
|---|---|
| main | `Status: Project setup complete` |
| proposal | `Status: Proposal under review` |

## How it was detected
- The Pull Request on GitHub showed "This branch has conflicts that must be resolved".
- Running **Git: Merge Branch → main** on `proposal` in VS Code produced
  conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) in `README.md`.

## How it was resolved
1. Switched to `proposal` and merged `main` into it.
2. Opened `README.md` and reviewed both versions.
3. Both changes were valid, so I combined them manually into one line:
   `Status: Project setup complete; proposal under review`
4. Deleted all conflict markers, saved, staged `README.md`, and committed the merge.
5. Pushed `proposal`; the PR conflict warning disappeared.

## Lesson learned
Edits to the same line on two branches cannot be auto-merged. Merging `main`
into the feature branch regularly surfaces conflicts early, when they are small.