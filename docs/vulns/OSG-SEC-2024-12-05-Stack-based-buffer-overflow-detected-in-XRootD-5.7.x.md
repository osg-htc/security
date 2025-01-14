# OSG-SEC-2024-12-05 Stack-based buffer overflow detected in XRootD 5.7.x

Dear OSG Security Contacts,

TLP:GREEN 

XRootD team has announced a security vulnerability in XRootD 5.7.x. This vulnerability is a network-reachable stack-based buffer overflow that could allow an attacker to crash vulnerable XRootD installs.

The official advisory[1] will be released to coincide with the public announcement of the XrootD 5.7.2 release. This security announcement is being sent to give time for sites to update prior to the official announcement; as such this announcement will not be publicly posted on our website until the official XRootD advisory is posted.

## IMPACTED VERSIONS:
XRootD 5.7.0 and 5.7.1

## WHAT ARE THE VULNERABILITIES:
This vulnerability consists in a stack-based buffer overflow coming from
std::regex which may crash when matching very long lines. This would allow
a malicious agent to cause a crash of either the client or the server when
processing very long URLs or HTTP headers.

## WHAT YOU SHOULD DO:
All sites running XRootD 5.7.x should update immediately.

XRootD 5.7.2 is currently available in the osg-testing repository [2]. It is also available via Github [3], XRootD release tarballs [4], and the XRootD repos [5].

XRootD 5.6.9 and earlier are unaffected.

## WORKAROUNDS

There is no known workaround for this vulnerability, users of XRootD 5.7.0 and 5.7.1 should upgrade to XRootD 5.7.2.

## REFERENCES
[1] https://github.com/xrootd/xrootd/security/advisories/GHSA-hrvf-4x86-8xrq 
[2] https://osg-htc.org/docs/common/yum/#repositories
[3] https://github.com/xrootd/xrootd/releases/tag/v5.7.2
[4] https://xrootd.web.cern.ch/download/v5.7.2/xrootd-5.7.2.tar.gz 
[5] http://xrootd.org/dload.html#official-rpm-repositories

Please contact the OSG security team at security@osg-htc.org if you have any questions or concerns.

OSG Security Team 
