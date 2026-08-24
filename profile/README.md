<div align="center">

<img src="./draugr-emblem.png" alt="" width="112" height="112" />

# Draugr

**Describe your app. Draugr figures out the rest.**

Run Trivy, Semgrep, Gitleaks and more from one file.<br>
One SARIF report, one pass/fail gate, findings ranked by real risk.

[draugr.dev](https://draugr.dev/) · [Documentation](https://draugr.dev/docs/) · [Blog](https://draugr.dev/blog/) · [Contact](https://draugr.dev/contact/)

</div>

---

Wiring SAST, SCA, secret, IaC and container scanners into a pipeline by hand means five tools to
configure, five outputs to read, and no answer to the only question being asked: **can this ship?**

You declare what you already know — where the repositories are, what images it builds, what it
exposes, what infrastructure it runs on. Draugr works out which checks apply, runs the right tool
for each, and produces evidence you can hand to somebody else.

```bash
curl -fsSL https://draugr.dev/install.sh | sh   # verifies the signature before it installs
draugr tools install                            # the scanners, pinned and checksum-verified
draugr scan .
```

[![Terminal output from draugr scan: a FAIL verdict, counts across priorities P1 to P4, a per-control table of severities, and a ranked fix-first list giving each finding's priority, severity, score, rule, control, scanner and file location.](https://raw.githubusercontent.com/draugr-dev/draugr/main/contrib/demo/scan.png)](https://github.com/draugr-dev/draugr)

**Priority is not severity.** P1–P4 weighs a finding against the component's exposure and
criticality — the part no scanner can compute, because it is not in the code. The same CVE is
act-now on an internet-facing service and backlog on an internal tool, and the descriptor is what
says which is which.

## The repositories

|  |  |
| --- | --- |
| **[draugr](https://github.com/draugr-dev/draugr)** | The CLI, and everything that runs in your pipeline. Go, Apache-2.0, signed releases with SBOMs and build provenance. |
| **[draugr-demo](https://github.com/draugr-dev/draugr-demo)** | A deliberately vulnerable app where every control lights up. Useful for evaluating **any** scanner: the findings are planted, stable, and each is documented with the class of tool that should catch it. |

## What it does not promise

A `PASS` means nothing crossed the thresholds you set, using the scanners that ran. It is not a
guarantee that an application is secure, and no tool can give you one — scanners have their own
coverage limits, and a repository scan reads the committed revision rather than what is deployed.
What Draugr adds is that the answer is reproducible, the reasoning is written down, and the
evidence is there when somebody asks who decided a finding was acceptable, and when.

<div align="center">

Security issue? See the [security policy](https://github.com/draugr-dev/.github/blob/main/SECURITY.md).

</div>
