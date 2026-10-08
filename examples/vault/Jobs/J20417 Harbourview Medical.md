---
type: job
job: J20417
aliases: ["J20417"]
customer: Harbourview Medical
model: SB-2000-DUAL-KI
enclosure: 90x72x36 ALU N3R
qty: 1
amperage: 2000
status: Drawing Check
reference: "[[J20112 Eastlake Hospital]]"
started: 2026-09-02
due: 2026-09-18
source_path: J:\Jobs\J20417 Harbourview Medical
parts_used:
  - "[[240-71136]]"
  - "[[240-71140]]"
  - "[[250-71201]]"
  - "[[200-30018]]"
---

# J20417 Harbourview Medical

## Release form summary
- **Job No:** J20417
- **Job Name:** Harbourview Medical, main switchboard
- **Model:** SB-2000-DUAL-KI
- **Enclosure:** 90 x 72 x 36 in, aluminium, outdoor rated
- **Qty:** 1
- **Amperage:** 2000 A

## Reference
[[J20112 Eastlake Hospital]]

- **What is reused:** enclosure frame, door set, main bus arrangement.
- **What is different:** second incoming source with a key interlock; cable-support bracket moved for the larger lugs.

## Parts Changed
*Filled in automatically when the job is finished: a comparison against the reference job's BOM.*

| Part | Change |
|---|---|
| [[240-71136]] | New. Cable-support bracket, replaces the reference job's bracket |
| [[240-71140]] | New. Interlock mounting plate |
| [[250-71201]] | New. Copper link between the two mains |
| [[200-30018]] | Reused from stock |

## Decisions
- Key interlock mounted on the left main to keep the handle clear of the door stiffener.

## Open Questions
- [ ] Confirm lug spacing on the second source with the electrical designer.

## Work Log

```dataview
LIST WITHOUT ID L.text
FROM "Daily Notes"
FLATTEN file.lists AS L
WHERE L.job = this.job
SORT L.text DESC
```
