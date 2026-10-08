---
name: job-review
description: Set up a job review. Opens the job's top-level SolidWorks assembly and prints the release form plus the first two pages of the matching electrical drawing set. Use when asked "let's review J20417", "review J20417-01", "set me up to review <job>", or otherwise asked to start a design review on a job number.
---

# Job Review

Pre-review setup. One phrase, `let's review J20417`, puts the top-level assembly on screen and the release form and electrical drawing on paper, so the model can be checked against the paperwork.

## What it does

1. **Opens the top-level assembly** from the job's CAD folder in SolidWorks.
2. **Prints the release form** (the sheet named `Form`).
3. **Prints pages 1–2 of the matching electrical drawing set.**

## Procedure

Run the resolver first. It touches nothing:

```
python scripts/review_job.py <JOB> --plan
```

Then:

1. **Show the plan and wait for a go.** Print jobs cannot be cancelled from a desk. Show the assembly path, the release form's name, the drawing set's name and its page count.
2. **Open the assembly**: `--open`. SolidWorks may take a while on a large assembly. That is normal; do not kill it.
3. **Print**: `--print`. Report what was queued.
4. **Log it** to today's daily note with `[job:: <JOB>] [kind:: review]`, per the standing auto-log rule.

`--open` and `--print` can be passed together once the go-ahead is given.

## How the pieces are found

- **Job root.** From the vault note's `source_path:` field, falling back to a search of the jobs folder for the job number. Handles `J20417-01` living inside a folder named plain `J20417`.
- **Top-level assembly.** The assembly whose number starts with the top-level prefix, under every CAD folder in the job, skipping archive and backup folders. Covers all three mechanical folder layouts. A variant suffix on the job number narrows it to that variant's folder.
- **Release form.** The variant's own form when a variant is given; otherwise the single form matching the job.
- **Electrical drawing set.** Matched to the model number on the release form.

## Gotchas

- **The model number is in two cells, and only one is right.** On one job the first cell read `...-V3-...` while the second cell and the actual drawing both read `...-U3-G-...`. The first matched no drawing file. The script uses the second and falls back to the first only with a loud warning.
- **Drawing file names carry a revision that the model number does not** (`... R1.3 - SET.pdf` against the bare model), and some have no revision at all. The matcher strips punctuation and compares the part before the revision in both directions.
- **The printer name has two forms and they are not interchangeable.** The spreadsheet program takes the display form; the print library takes the server form and rejects the other as invalid. Passing one name to both produces a confusing "printed 1 of 2": the form prints and the drawing silently fails. The script derives both from the default printer. Do not merge them.
- **Everything prints black and white.** Colour needs admin rights, so a colour drawing comes out greyscale. If colour is needed, I open it myself and switch it on.
- **The jobs folder is read-only.** This skill only reads from it and sends print jobs.
