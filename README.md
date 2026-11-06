# Security

[![Build Status](https://travis-ci.org/opensciencegrid/security.svg?branch=master)](https://travis-ci.org/opensciencegrid/security)

This repo is the OSG security team's website.


## Drafting vulnerability announcements with an AI coding agent

The repo includes an `osg-cve-announcement` skill that researches a CVE
(CVE.org, NVD, Red Hat, CISA KEV, plus any URL you give it) and writes a new
`docs/vulns/OSG-SEC-YYYY-MM-DD.md` in the same style as recent announcements,
then adds it to `mkdocs.yml` and `docs/OSGSecurityAnnouncements.md`.

The skill lives in `.agents/skills/osg-cve-announcement/` and is symlinked
into `.claude/skills/`. Start the agent from the repository root, then:

- Claude Code: `/osg-cve-announcement CVE-2026-12345 https://vendor.example/advisory`
- OpenAI Codex (CLI, IDE, or ChatGPT Codex cloud): `$osg-cve-announcement CVE-2026-12345 https://vendor.example/advisory`
- OpenCode: ask "Use the osg-cve-announcement skill for CVE-2026-12345 https://vendor.example/advisory"

It also writes the plain-text email body to `notify/<ID>.txt` (ASCII only,
as `osg-notify` requires) and prints the `osg-notify` commands (test,
dry run, production) for emailing it to security contacts. To regenerate
the email after editing the page:

    python3 .agents/skills/osg-cve-announcement/scripts/to_notify.py docs/vulns/OSG-SEC-YYYY-MM-DD.md

Always review the draft against the cited sources before publishing.
