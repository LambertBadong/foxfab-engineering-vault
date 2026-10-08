---
name: read-the-named-sheet
description: When reading a release form, select the sheet by name, never the active one
metadata:
  type: feedback
---

When reading a job's release form, **always open the sheet called "Form" by name**. Never use whichever sheet happens to be active.

**Why:** The workbook has several sheets: the form, a quality checklist, the nameplate, a front page and some lists. The active one is simply the tab that was open when someone last saved the file. On many older jobs that is the nameplate sheet, which has a completely different cell layout. The cell map (job number, model, job name, amperage, enclosure size, material, rating, quantity) is only valid on the form sheet.

This bit during a bulk import of 48 past jobs. The active sheet was the nameplate for many of them, so the model, enclosure, quantity and amperage came back blank. Nothing raised an error.

**How to apply:**

- Select the sheet by name. A missing sheet should raise, and that case is handled explicitly.
- Check the sheet exists before reading. If it does not, ask. Do not fall back to the active sheet.
- The same assumption is probably hiding in the older skills that read this form. Check them when they are next touched.
