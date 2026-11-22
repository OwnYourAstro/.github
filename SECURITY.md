# Security policy

## Reporting a vulnerability

Do not open a public issue for a security problem. Report it privately using
GitHub's [private vulnerability reporting](https://docs.github.com/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
on the affected repository, or contact a maintainer directly.

Please include the affected version or commit, a description of the issue, and
the smallest reproduction you can manage. We will acknowledge the report,
investigate, and coordinate disclosure with you.

## What counts as a security issue here

- A crafted codeplug or archive file that causes the software to read or write
  outside its intended memory, execute code, or corrupt unrelated data.
- A path traversal or archive-extraction bug in file handling.
- A bug that causes the software to write unintended data to a radio.
- Leakage of credentials, keys, or personal data from logs, captures, or
  temporary files.
- A supply-chain problem in a dependency.

## Bench safety

This software talks to radio hardware and can change a radio's configuration.
Two rules apply to every report, test, and pull request:

1. **Test on a bench.** Never test against a radio on a live system, and never
   on a system you are not authorized to touch.
2. **Assume a write can brick.** Destructive operations need a backup, a
   dry-run, and a way back before they are exercised on hardware you care
   about.

## Supported versions

The project is alpha. Until a release is tagged, fixes land on the default
branch and there are no backports.

## Disclosure

We aim to fix confirmed issues before public disclosure and will credit
reporters who want credit. Out of scope: reports that require material
obtained in violation of law or contract, and reports about the operation of
third-party radio systems.
