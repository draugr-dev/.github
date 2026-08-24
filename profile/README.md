<div align="center">

<img src="./draugr-emblem.png" alt="" width="112" height="112" />

# Draugr

**Describe your app. Draugr figures out the rest.**

Find the security problems in what you ship — without being a security engineer.

[draugr.dev](https://draugr.dev/) · [Documentation](https://draugr.dev/docs/) · [Blog](https://draugr.dev/blog/) · [Contact](https://draugr.dev/contact/)

</div>

---

Every application carries problems nobody put there on purpose: a library that turned out to have
a hole in it, a password committed by accident, a server setting that leaves a door open. Draugr
finds them, works out which ones actually matter for **your** app, and answers the question you
are really asking before a release — **is this safe to ship?**

It runs the established open-source scanners for you — Trivy, Semgrep, Gitleaks and others — so
there is nothing to choose between, wire up, or read five of. You describe what you built, once,
in one file. Draugr picks the checks that apply and hands back a short ordered list and a yes or
no.

```bash
curl -fsSL https://draugr.dev/install.sh | sh   # checks the signature before it installs
draugr tools install                            # fetches the scanners, verified as it goes
draugr scan .                                   # your libraries, your code, leaked secrets, your config
```

No account, and your code is never uploaded anywhere — the scanners run where you run them, and
the only thing crossing the network is the rules and vulnerability data coming down.

[![Terminal output from a Draugr scan. A large FAIL, then how many problems fall into each of four bands from act-now to track. Below that, one line per kind of check saying whether it passed, and a list of what to fix first — each row naming the problem, how serious it is, and the file and line it is in.](https://raw.githubusercontent.com/draugr-dev/draugr/main/contrib/demo/scan.png)](https://github.com/draugr-dev/draugr)

It looks at the libraries you depend on, the code you wrote, passwords and keys committed by
accident, the settings that describe your servers, what is inside your containers, the licenses
attached to code you did not write, and your app while it is running.
[The full list is on the site](https://draugr.dev/#what-it-checks).

**A scanner's "critical" is not your critical.** Those words describe a flaw in the abstract —
how bad it could be at its worst, anywhere. They know nothing about you. The same flaw is drop
everything in the service strangers can reach and next month in the internal tool three people
use, and no scanner can tell those apart, because the difference is not in the code. It is in the
file you wrote, which is why Draugr can rank the list instead of just printing it.

## The repositories

|  |  |
| --- | --- |
| **[draugr](https://github.com/draugr-dev/draugr)** | The tool itself, and everything that runs in your pipeline. Go, Apache-2.0. Every release is signed, and the installer checks that signature before it installs anything. |
| **[draugr-demo](https://github.com/draugr-dev/draugr-demo)** | A small app with security problems deliberately planted in it, so you can watch a scanner find them. Useful for trying **any** tool, not only this one: the problems are documented, so you already know the right answer. |

## What it does not promise

A pass means nothing crossed the limits you set, using the checks that ran. It is not a promise
that your application is secure, and no tool can honestly make you one — every scanner has gaps,
and a scan of a repository reads the code that was committed rather than whatever is running right
now. What Draugr adds is that the answer is the same every time, the reasoning is written down,
and the evidence is still there months later when somebody asks who decided a problem was
acceptable, and when.

<div align="center">

Security issue? See the [security policy](https://github.com/draugr-dev/.github/blob/main/SECURITY.md).

</div>
