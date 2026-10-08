# Standing instructions (excerpt)

*Loaded at the start of every session, before anything I type. Rewritten for publication; paths are invented.*

## Who I am

- Mechanical designer. My part numbers start with a personal two-digit prefix; parts with that prefix are mine and file under my folder.
- Personal memory folder: `~/.claude/projects/<vault>/memory/`.

## Preferences

- **Log without asking.** Every tangible request goes into today's daily note, under the agent's activity section. Tag it with the job number when it belongs to a job. No "shall I log this?".
- **Daily rituals.** "Good morning" or "starting my day" runs the morning briefing and starts the CAD watcher, with no confirmation. "Logging off" or "EOD" stops the watcher and runs the memory sweep.
- **Fridays.** The end-of-day routine also consolidates memory.

## Where things live

- I work in the local copy of the vault. A second copy sits on the shared drive.
- There is no automatic sync between them. The end-of-day routine does a one-way, additive copy.

## End of day: backup

1. List what the shared copy has that is **newer** than mine. Pull those in first, or at least name them in the summary.
2. Copy local to shared. Additive only: never delete at the destination, and never overwrite a file that is newer there.
3. Commit and push **my own repository only**.
4. Log both steps in today's note, with the commit id.

Why step 1 and the "never overwrite newer" rule exist: an earlier version of this copy replaced a fix a colleague had made twenty minutes before. Their work had to be rebuilt from an email.

## Hard limits

- **Never push to a shared team repository from the end-of-day routine.** Anything bound for a team repository goes through a branch and a pull request that a colleague approves.
- **Never auto-merge.**
- **The job archive is read-only.** Read and copy out. Do not edit, move, rename or delete there. The only exceptions are the named tools that are approved to write a job's BOM.
- **Check the clock before logging.** Never invent a timestamp.
- **Never exit my SolidWorks session,** and close only the documents a script opened itself.
- **Ask before any long-running CAD operation.**
- **Test in the sandbox folder,** never in a live job, until I say a thing is ready for live testing.
