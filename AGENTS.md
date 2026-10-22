# Agent notes

This repository is the OSG Security team's MkDocs website.

- Vulnerability announcements live in `docs/vulns/OSG-SEC-YYYY-MM-DD.md` and
  are listed newest first in both `mkdocs.yml` (under `Announcement Details`)
  and the table in `docs/OSGSecurityAnnouncements.md`.
- To draft a new announcement from a CVE ID (and optional advisory URL), use
  the `osg-cve-announcement` skill in `.agents/skills/osg-cve-announcement/`
  (also linked from `.claude/skills/`). Read its `SKILL.md` and follow it even
  if your tool does not load skills automatically.
- Announcements are also emailed with `osg-notify`
  (https://github.com/opensciencegrid/topology), which accepts printable ASCII
  only, so keep announcement text ASCII. Never run `osg-notify` yourself.
