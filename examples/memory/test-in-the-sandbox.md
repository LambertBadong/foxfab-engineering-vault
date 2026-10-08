---
name: test-in-the-sandbox
description: All testing goes in the sandbox folder, never a live job folder, until I explicitly say a thing is ready for live testing
metadata:
  type: feedback
---

**All testing happens in the sandbox folder.** This is a standing default, not a per-task instruction. Live testing is opt-in, and I opt in explicitly, per thing. Silence is not permission, and "it worked and I cleaned up afterwards" is not a defence.

## The sandbox is already stocked

The sandbox holds more than thirty copies of real job folders, including small, medium and large ones kept for exactly this. There is never a reason to reach into the live archive to test something. If a test needs a job with particular contents, a sandbox copy almost certainly has it.

## What went wrong (the shape to watch for)

A helper agent, checking a new logging command, wrote a log file into a **live** job folder, confirmed it worked, then deleted it. The clean-up held, but the write happened.

The fault was in the brief, not the worker. The task said "the archive is read-only except the job's own log file", which read as permission. **When delegating, name the sandbox path and say live folders are off limits.** A helper has none of this context and will do exactly what the prompt allows.

## Second time: removing a test escape hatch

A change made a reporting feature ignore a "send it somewhere else" argument, which was correct: the screen must not choose where reports go. But one of its own tests still relied on that argument. The next run wrote a real report into the live reports folder. It was moved out minutes later.

This time the brief was right, and it happened anyway.

**When a change removes a way to redirect a write, every test that used it becomes a live write.**

**How to apply:**

- Use the sandbox by default. Ask before anything else.
- In a brief to a helper, state the sandbox path and the prohibition in the same sentence.
- When removing a redirect or an override, search the tests for it first.
