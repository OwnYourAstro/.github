<div align="center">

# OwnYourAstro

**Right to repair for Motorola Astro 25 radios.**

An independent, open-source, MIT-licensed clean-room implementation of
Customer Programming Software (CPS) and Depot tooling for Astro 25
portable and mobile radios.

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Clean room](https://img.shields.io/badge/method-clean--room-6f42c1.svg)](docs/clean-room.md)

</div>

---

## Why this exists

A radio you own should be a radio you can configure. Today, programming an
Astro 25 portable or mobile depends on vendor software that is tied to
specific Windows releases, specific cables, specific account entitlements, and
a support lifecycle you do not control. When that software stops being
available or stops running, working hardware becomes e-waste and public-safety
volunteers, hobbyists, and small shops are left with no lawful path forward.

OwnYourAstro exists to give owners that path back:

- read and back up your own codeplug before you lose it,
- inspect and edit your own configuration,
- move configurations between radios you own,
- keep interoperable equipment in service well past vendor end-of-life.

This is a right-to-repair project. It is not a piracy project, and it is not
affiliated with, endorsed by, or sponsored by Motorola Solutions.

## What we are building

| Project | Role | Status |
| --- | --- | --- |
| [**OpenDepotCore**](https://github.com/OwnYourAstro/OpenDepotCore) | Core engine: codeplug model, file formats, transport, validation, and depot-level operations | Alpha |
| [**OpenDepot**](https://github.com/OwnYourAstro/OpenDepot) | Cross-platform GUI on top of the core. Desktop first; web and Android frontends later | Alpha |
| [**Docs & specs**](https://github.com/OwnYourAstro/OpenDepot/tree/master/docs) | Clean-room behavioral specifications and test vectors that both projects build against | In progress |

Project site: [ownyourastro.com](https://ownyourastro.com).

`OpenDepotCore` holds the logic. `OpenDepot` is a client of it, so that a
desktop build, a web build, and an Android build can share one implementation
of the hard parts.

## Clean room, not a leak

Everything here is written from scratch against observed behavior, not against
vendor source.

1. **Observation.** We study lawfully obtained hardware, publicly available
   material, and our own captured traffic.
2. **Specification.** Findings are written down as behavioral descriptions and
   test vectors — no copied code, no vendor binaries.
3. **Implementation.** Code is written from the specification by people working
   from that document, and reviewed for provenance.
4. **Verification.** Implementations are checked against the recorded
   observations on real hardware on a bench.

The full process, including what may and may not be contributed, is in
[`CONTRIBUTING.md`](CONTRIBUTING.md) and [`docs/clean-room.md`](docs/clean-room.md).

Every line in these repositories is MIT-licensed and contributed under the
Developer Certificate of Origin. We do not accept vendor source, leaked
material, decompiled listings, NDA material, or codeplugs belonging to other
people.

## Scope

In scope: Astro 25 portable and mobile radios, their codeplug structure, their
programming transport, tuning and alignment data, and the depot-level
operations that service centers perform on equipment they are authorized to
service.

Explicitly out of scope: distributing Motorola software, firmware, or
entitlement material; helping anyone operate on radio systems they are not
licensed or authorized to use; and anything that depends on material obtained
in violation of law or contract.

See [`docs/scope.md`](docs/scope.md) for detail.

## Status

Alpha. The core decodes and edits codeplugs, represents every record in a
CPS-style model (149 tags across the test corpus), and implements the native
serial/PPP/RCMP transport without a vendor DLL. Reads and writes have been
validated on a single XTS 2500 (137 records, identical read-back). The Qt 6
desktop app builds on the core.

Only one model and band has been exercised on hardware. Firmware flashing is
not supported. Keep a verified backup and never force a refused write.

Start with [OpenDepotCore](https://github.com/OwnYourAstro/OpenDepotCore) for
the engine and [OpenDepot](https://github.com/OwnYourAstro/OpenDepot) for the
desktop app. Watch the [roadmap](docs/roadmap.md) for what is next.

If you have a radio on a bench, a documented observation, or clean-room
experience, you are exactly who this project needs.

## Get involved

- [Contributing and the clean-room rules](CONTRIBUTING.md)
- [Project scope](docs/scope.md)
- [Roadmap](docs/roadmap.md)
- [Architecture notes](docs/architecture.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)
- [Security policy](SECURITY.md)

## Legal

OwnYourAstro is an independent project. It is not affiliated with, endorsed
by, or sponsored by Motorola Solutions, Inc. "Motorola", "ASTRO", "XTS",
"XTL", and "APX" are trademarks of their respective owners and are used here
only to describe interoperability targets. See [`TRADEMARKS.md`](TRADEMARKS.md).

You are responsible for the radios you program, the frequencies you transmit
on, and the licenses that apply to them. Programming a transmitter incorrectly
can take it off the air, take it out of compliance, or interfere with users who
depend on it. Test on a bench, not on a live system.
