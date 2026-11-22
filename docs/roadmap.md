# Roadmap

This is intent, not a schedule. Everything below assumes bench hardware, a
written clean-room spec, and passing tests before it ships.

## Phase 0 — Foundation

- [x] Organization, policies, and clean-room process
- [ ] Repository layout for `OpenDepotCore` and `OpenDepot`
- [ ] Core API sketch and format-description conventions
- [ ] First specification: codeplug container and a read-only round trip

## Phase 1 — Read-only

- [ ] Identify a connected radio and report model, firmware, and serial
- [ ] Read a codeplug and represent it losslessly
- [ ] Export to an open, documented interchange format
- [ ] Verify a re-read matches the first read across a bench sample

Read-only first. Nothing in this phase writes to hardware.

## Phase 2 — Write, carefully

- [ ] Validate before write, with a dry-run diff
- [ ] Write back a configuration that was read unmodified
- [ ] Write back a minimal edit (for example, one channel name)
- [ ] Interrupted-session recovery and post-write verification
- [ ] Bench matrix across supported models and firmware

## Phase 3 — Usable GUI

- [ ] `OpenDepot` desktop client on the core
- [ ] Zone/channel editing, scan lists, contacts, and button assignments
- [ ] Import and export, backup and restore
- [ ] Packaging for Windows first, then Linux and macOS

## Phase 4 — Depot workflows

- [ ] Tuning and alignment read/write with explicit safeguards
- [ ] Depot-level operations for authorized service use
- [ ] Audit logging for every destructive operation

## Phase 5 — Other frontends

- [ ] Web frontend over the core
- [ ] Android frontend over the core
- [ ] Shared conformance test suite across all frontends

## Non-goals

- Beating vendor CPS at every edge case before shipping anything.
- Supporting every Astro 25 variant on day one.
- Anything listed as out of scope in [`scope.md`](scope.md).

## How to help right now

The highest-value contributions are observation records and specifications
from people with hardware on a bench, and clean-room implementers willing to
work from text alone. See [`CONTRIBUTING.md`](../CONTRIBUTING.md).
