\# OSG-SEC-2026-09-29-Linux BTR / Spectre-v2–CVE-2026-64507 and CVE-2026-64508

Dear OSG Security Contacts,

A flaw was found in the Linux kernel's and Berkeley Packet Filter (BPF) Just-In-Time (JIT) compiler \[1\]\[2\]. The vulnerabilities involve the BPFJIT compiler reusing executable memory without adequately clearing stale CPU branch-prediction state, potentially allowing disclosure of sensitive information. Public proof-of-concept (PoC) exploit code is available \[3\].

\#\# IMPACTED VERSIONS:

RHEL: 7,8,9 and 10 are affected.  
Ubuntu:  Multiple Ubuntu kernel versions are affected. See references \[4\] and \[5\] for the affected versions and available security updates.

\#\# WHAT ARE THE VULNERABILITIES:

BTR is a Spectre-v2-style attack that abuses stale CPU branch-prediction state when executable memory used by the BPF JIT is reused. An unprivileged local process can potentially exploit this behavior to disclose sensitive memory across security boundaries. The published PoC was specifically tested against Ubuntu 24.04 with Linux kernel 6.14.0-27-generic.

The demonstrated impact is sensitive memory disclosure rather than direct local privilege escalation (LPE). Researchers demonstrated that an unprivileged process could locate a privileged process and recover a root password hash from memory. However, this is likely only one of the potential types of sensitive data that is at risk.

Obtaining a password hash does not by itself provide root privileges. However, if the associated password is weak and can be recovered through offline password cracking, the disclosed credential could potentially be used for subsequent privilege escalation or unauthorized access.

\#\# MITIGATION :

No effective vendor-documented workaround has been identified for affected RHEL systems at this time.  
Disabling unprivileged eBPF alone should not be considered sufficient because the demonstrated attack uses classic BPF (cBPF).

\#\# WHAT YOU SHOULD DO:

Ubuntu: Apply the applicable Canonical kernel security updates addressing CVE-2026-64507 and CVE-2026-64508.  
RHEL: Continue monitoring Red Hat for kernel security updates and apply the vendor-provided kernel fix when available.  
Reboot into the updated kernel after applying vendor security updates.

Where a usable root password is configured, sites should consider performing an authorized offline password-strength audit of the root password hash using an established password-auditing tool such as Hashcat\[6\] or John the Ripper\[7\] and an appropriate common-password corpus. Any weak passwords identified during the audit should be replaced with strong, unique credentials.

\#\# REFERENCES

\[1\] [https\://access.redhat.com/security/cve/cve-2026-64507](https://access.redhat.com/security/cve/cve-2026-64507)   
\[2\] [https\://access.redhat.com/security/cve/cve-2026-64508](https://access.redhat.com/security/cve/cve-2026-64508)   
\[3\] [https\://thehackernews.com/2026/09/new-spectre-v2-btr-attack-leaks-linux.html](https://thehackernews.com/2026/09/new-spectre-v2-btr-attack-leaks-linux.html)  
\[4 \][https\://ubuntu.com/security/CVE-2026-64507](https://ubuntu.com/security/CVE-2026-64507)  
\[5 \][https\://ubuntu.com/security/CVE-2026-64508](https://ubuntu.com/security/CVE-2026-64508)    
\[6\] [https\://hashcat.net/hashcat/](https://hashcat.net/hashcat/)  
\[7\] [https\://www\.openwall.com/john/](https://www.openwall.com/john/)

Please contact the OSG security team at security@osg-htc.org if you have any questions or concerns.  
OSG Security Team  
