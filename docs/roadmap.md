# Roadmap

This is intent, not a schedule. Everything below assumes bench hardware, a
written clean-room spec, and passing tests before it ships.

## Current status (November 2026)

Alpha. `OpenDepotCore` reads, decodes, edits, and writes codeplugs, represents
every record in a CPS-style model (149 tags across the test corpus), and has a
native serial/PPP/RCMP transport. `OpenDepot` is a working Qt 6 desktop client.
Read/write is validated on **one** XTS 2500; firmware flashing is out of scope.

## Phase 0 — Foundation

- [x] Organization, policies, and clean-room process
- [x] Repository layout for `OpenDepotCore` and `OpenDepot`
- [x] Core API sketch and format-description conventions
- [x] First specification: codeplug container and a read-only round trip

## Phase 1 — Read-only

- [x] Identify a connected radio and report model, firmware, and serial
- [x] Read a codeplug and represent it losslessly
- [x] Export a decoded model (`--model`, `--schema`) and raw records
- [x] Verify a re-read matches the first read on the bench radio

Read-only first. The native read path never writes; writes are a separate,
explicitly validated path.

## Phase 2 — Write, carefully

- [x] Validate before write, with a dry-run diff and completeness guard
- [x] Write back a configuration that was read unmodified
- [x] Write back a minimal edit (for example, one channel name)
- [x] Return the radio to AT mode after every session, with post-write identity
      verification
- [ ] Bench matrix across supported models and firmware
- [ ] Full record-level read-back comparison after every write in the GUI

## Phase 3 — Usable GUI

- [x] `OpenDepot` desktop client on the core
- [x] Zone/channel editing, plus alias and list views
- [ ] Full scan-list, contact, and button-assignment editing
- [x] Backup and restore
- [ ] Import and export beyond `.cpg`
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
