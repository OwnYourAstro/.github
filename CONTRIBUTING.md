# Contributing to OwnYourAstro

OwnYourAstro builds open, MIT-licensed CPS and Depot tooling for Astro 25
radios. Because the goal is interoperability with a vendor's closed product,
the *method* matters as much as the result. This document is the rulebook.

Read [`docs/clean-room.md`](docs/clean-room.md) before your first pull
request. If anything here is unclear, ask first — an issue costs nothing, and
a contaminated contribution can cost the whole project.

## The short version

1. **Write code from specifications, not from vendor artifacts.**
2. **Never commit vendor software, firmware, decompiled listings, leaked
   source, or someone else's codeplug.**
3. **Record where every behavioral claim came from.**
4. **Sign off every commit** (`git commit -s`) to certify the Developer
   Certificate of Origin.
5. **License contributions under MIT.**

## What you may contribute

- Original source code you wrote yourself.
- Behavioral specifications derived from your own bench observations.
- Test vectors, captures, and sample data that you generated from hardware
  you own and are authorized to service, with no third-party personal data.
- Documentation and tooling you wrote yourself.
- Publicly available information that carries no confidentiality obligation
  — datasheets, standards documents, published specifications — cited in the
  pull request.

## What you may not contribute

- Any Motorola source code, object code, installer, DLL, firmware image, or
  update package.
- Decompiled or disassembled listings, or anything copied out of them.
- Material received under an NDA, service contract, or partner agreement.
- Codeplugs, tuning files, or archives belonging to another person or
  organization.
- Content scraped from vendor portals or copied from vendor documentation.
- Entitlement data, license keys, flashkeys, or feature-enablement material.
- Code, spec text, or test data from another clean-room project whose license
  is incompatible with MIT.

If you are unsure whether something is allowed, it is not allowed until a
maintainer says otherwise in writing.

## The clean-room split

Work is split so that the people writing code are not the people reading
vendor artifacts.

**Analysts** examine hardware and observable behavior and write it down as
prose, tables, and test vectors. Analysts do not write product code.

**Implementers** write code from the written specification. They work from
documentation and test vectors only, and they do not consult vendor binaries
or decompiled output.

**Reviewers** check both sides: that the spec is adequately sourced, and that
the implementation is traceable to the spec rather than to a vendor artifact.

A single person may hold more than one role over time, but never on the same
feature at the same time, and never in a way that lets vendor artifacts reach
the implementation.

## Specification format

Behavioral specs live in the `docs/` tree of the repository they belong to and
should state:

- **Subject** — the radio model, firmware family, cable, or file type.
- **Observation** — what was done and what was seen, in enough detail that
  another person with the same hardware can reproduce it.
- **Confidence** — `confirmed`, `probable`, or `unverified`.
- **Provenance** — hardware owned or authorized by the contributor, public
  document with a citation, or original capture.
- **Open questions** — anything the observation did not settle.

Specs describe behavior. They do not paste vendor text, code, or strings
beyond what is necessary to implement interoperability.

## Pull request checklist

- [ ] The change is original work, or derived only from a written spec in this
      organization.
- [ ] No vendor binaries, firmware, decompiled output, or third-party
      codeplugs are included.
- [ ] New behavioral claims link to a spec section, and the spec states its
      provenance.
- [ ] Commits are signed off with `git commit -s`.
- [ ] The change is licensed under MIT.
- [ ] Hardware-dependent behavior was tested on a bench, not on a live system.

## Commit sign-off

All commits must carry a `Signed-off-by` trailer certifying the
[Developer Certificate of Origin 1.1](https://developercertificate.org/):

```
git commit -s -m "core: parse channel table header"
```

`git commit -s` adds the trailer using your configured `user.name` and
`user.email`. Use an identity you are entitled to use.

## Code and review conventions

- Keep the core (`OpenDepotCore`) free of UI and platform assumptions so the
  desktop, web, and Android frontends can share it.
- Treat radio writes as destructive operations: validate, dry-run, and require
  explicit confirmation before anything is sent to hardware.
- Prefer explicit, documented binary layouts over clever parsing. Someone
  should be able to read a format definition and understand it a year later.
- Add a test vector for every format or protocol behavior you add.
- Do not add dependencies that cannot be built or audited from source.

## Reporting problems

- Bugs and feature requests: open an issue in the relevant repository using
  the templates.
- Security issues: follow [`SECURITY.md`](SECURITY.md). Do not open a public
  issue for a vulnerability.
- Conduct issues: see [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md).

## Licensing

By contributing you agree that your contribution is licensed under the MIT
License and that you have the right to submit it. See [`LICENSE`](LICENSE).
