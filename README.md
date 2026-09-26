# 🧠 Engineering Second Brain — Obsidian + Claude Code

> An Obsidian vault that acts as a shared "second brain" for a switchgear engineering team — with Claude Code as the engineer's assistant.

![Status](https://img.shields.io/badge/status-in%20daily%20production%20use-2ea44f)
![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?logo=obsidian&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?logo=anthropic&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?logo=powershell&logoColor=white)

> **Showcase repository.** The vault itself contains proprietary employer data (jobs, customers, part numbers, design standards) and is kept private. This repo documents the system design.

---

## The idea

Engineering knowledge usually lives in people's heads, scattered spreadsheets and CAD folders. This vault turns it into a **linked, searchable second brain**: every job, every part and every day of work is a note, and the links between them answer questions like:

- *Which past jobs used this part?*
- *What changed between this job and its reference job?*
- *What did the team work on this week?*

## At a glance

| | |
|---|---|
| Jobs tracked | **75+** |
| Auto-generated, cross-linked part notes | **1,600+** |
| Daily notes | **125+** |
| CAD events auto-logged | **540+** |
| Timestamped log entries | **1,700+** |
| Shared AI memory rules | **14** |

## How it works

```
 Release form (Excel) ──► Claude Code ──► Job note (Templater)
                                 │
 Latest BOM (Excel) ─────────────┼──► Part notes (1 per part no.) + "Parts Changed" diff vs. reference job
                                 │
 CAD folders ──► Python CAD monitor ──► Daily note  ◄── Claude work-log entries (Dataview fields)
                                                  │
                                                  ▼
                         Dataview dashboards: Active Jobs · Parts Frequency · CAD Heatmap · Team Activity
```

1. **PARA structure** — Projects (one note per job), Resources (engineering reference: bend calculator, UL ampacity tables, busbar selection, UL 891/1008 notes, common drawing mistakes), Parts (one stub note per part number), Daily Notes, Meta (templates, dashboards, scripts, AI memory).
2. **Job intake** — "new job …" → Claude Code reads the production release form, fills the job template's frontmatter (model, enclosure, amperage, status…) and links the reference job.
3. **Job finish** — "I finished …" → Claude reads the latest BOM, creates/links every part note and diffs parts against the reference job. A *full-coverage rule* requires BOM rows, frontmatter links and body links to match.
4. **Live CAD monitor** — a Python watcher polls active jobs' CAD folders every 10 s and logs each new SolidWorks part/assembly to the day's note.
5. **Auditable AI work log** — every task Claude performs is logged with Dataview inline fields and rolled up per job and on heatmap calendars.
6. **Team rituals** — "Good morning" / "EOD" start and stop the watcher, sweep AI memory, and sync the vault via a hash-based three-way sync + Git.
7. **Status pipeline** — Imported → Started → Model Check → Drawing Check → Programming → Done → Archive.

## Tech

Obsidian (Dataview, DataviewJS, Templater, Tasks, Kanban, Periodic Notes, Heatmap Calendar, Linter) · Claude Code (project memory + skills) · Python · PowerShell · SolidWorks VBA · Git

## Related

- [Engineering Tool Hub](https://github.com/LamboProjects/engineering-tool-hub) — the desktop automation suite that works alongside this vault.

---

Built by **Lambert Badong** · [GitHub](https://github.com/LamboProjects)
