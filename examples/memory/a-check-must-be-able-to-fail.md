---
name: a-check-must-be-able-to-fail
description: A check that cannot tell success from absence is not a check. Five ways it happened, and how to catch each
metadata:
  type: feedback
---

**A check that cannot fail proves nothing, and it fails silently by passing.** This happened five separate ways over two days, each producing a perfectly plausible result.

**Why:** every one of these looked like success. None raised an error, none went red. The failure is not that verification breaks loudly. It keeps passing while measuring nothing.

## The five

1. **Two identical screenshots.** Two different states rendered to the same file size and the same checksum. The state had never been applied. Compare checksums; do not eyeball sizes. I read an identical byte count three times before treating it as a signal.

2. **Old data behind a fresh page.** The page was reloaded; the data file it reads was not. The new capture rendered against the previous data.

3. **Old code behind fresh data.** Then the script itself was cached, so an edit rendered as the version before it, which looks exactly like an edit that did nothing. Refresh everything the result depends on, not only the part that bit last time.

4. **An animation that never advances.** In the capture environment the animation clock does not move, so an element sized by a transition stays at its starting size. This was found only because a temporary outline, added to debug it, happened to force a redraw. A diagnostic that fixes the bug it is measuring is a finding, not a win.

5. **Assertions that could not fail.** Two shapes. A *negative* assertion that passed because the element was not there at all: "the banner does not show the full path" passed with no banner. And an assertion that was literally written as always-true.

## How to tell the test rig from the product

When a suite fails with **every positive assertion failing and every negative one passing**, suspect the rig, not the code. Twenty-one identical failures turned out to be one broken fixture.

**How to apply:**

- Before trusting a passing check, break the thing on purpose and confirm the check fails.
- Require the element to exist before asserting anything about its content.
- Never commit a placeholder assertion.
