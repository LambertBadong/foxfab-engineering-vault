---
name: record-every-mistake
description: Standing rule. Every mistake found and fixed is written to memory the same session, as a general rule and not a story
metadata:
  type: feedback
---

**When a mistake is found and fixed, write it down before moving on.**

I asked for this after a session where the same *shapes* of error kept coming back: "let's always remember mistakes and how we fixed them, so that when a similar error comes up in the future you will know exactly how to deal with it."

**Why:** the recurring cost is never the individual bug. It is working out the *diagnosis* again. The second time an error is swallowed by a handler, or a text-anchored edit takes a neighbour, the hours go into rediscovering how to see it, not into the fix. A note that names the shape turns a two-hour hunt into a five-minute check.

**How to apply:**

- **Write it the same session, not at the end of the day.** A fix explained an hour later has already lost the false trail that made it hard, and the false trail is the useful part.
- **Record the shape, not the story.** Not "the delete removed eleven functions"; that never recurs. "A text-anchored deletion can silently take neighbouring code; list what exists before and after" recurs constantly.
- **Include how it looked before it was understood.** The symptom is the lookup key. Next time, the symptom is what arrives first, with no hint that it belongs to this rule.
- **Include what made it invisible.** Most of these are not hard problems. They are problems with no visible failure. Name the thing that hid it.
- **Prefer updating an existing note** over adding a near-duplicate. Three thin files are worse than one thorough one.
- **Say what to check first next time**, in one line. That is the part that saves the hours.

**Also worth recording:** a claim that was carried and later disproved. A tool was once reported as saving files it did not save, repeated across several messages, and it was wrong. The evidence against it had been on disk the whole time. A wrong belief stated confidently costs more than a bug, because nobody goes looking for it. When something is corrected, record the correction, not only the eventual truth.
