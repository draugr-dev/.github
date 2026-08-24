# Security policy

Applies to every repository in this organization that does not carry its own.

## Reporting a vulnerability

**Do not open a public issue.** Report privately through
[GitHub Security Advisories](https://github.com/draugr-dev/draugr/security/advisories/new), or by
email to **security@draugr.dev**.

We aim to acknowledge a report within 3 business days, and to give a remediation timeline after
triage. What helps most:

- what the issue is and what it lets somebody do,
- how to reproduce it — a minimal proof of concept if you have one,
- the version or commit it affects.

## Before you report against `draugr-demo`

[`draugr-demo`](https://github.com/draugr-dev/draugr-demo) is **deliberately vulnerable**. The
injection, the unsafe `eval`, the known-vulnerable dependencies, the "private key", the
root-running container and the privileged pod are all planted, documented in its README, and
refreshed on every release. They are the fixture, not a defect — a scanner is only worth
evaluating against a case where the answer is already known.

Nothing there is deployed, and the credentials in it are fake. A finding in that repository does
not need reporting. A way to make it harm somebody who cloned it does.

## What we do about our own

Draugr is a security tool, and holding it to the standard it enforces is the least it can do.
Every change to the CLI is scanned by the latest *released* Draugr — dependency vulnerabilities,
leaked secrets, static analysis and infrastructure misconfiguration — with the results published
to that repository's **Security → Code scanning** tab where anybody can read them. Releases are
signed with keyless cosign and ship SBOMs and build provenance, and the install script verifies
that signature before it installs anything.

The [`draugr` repository's own policy](https://github.com/draugr-dev/draugr/blob/main/SECURITY.md)
has the detail, including how to verify a release yourself.
