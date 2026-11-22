# Scope

## In scope

### Hardware

Motorola Astro 25 portable and mobile radios, including the XTS and XTL
families and related Astro 25 models. Where a behavior is shared across a
family, the spec should say so rather than being duplicated per model.

### Feature areas

- **Codeplug model** — the data structure a radio is configured with:
  zones and channels, talkgroups, scan lists, contacts, signaling, button
  and menu assignments, and the metadata around them.
- **File formats** — the on-disk and on-wire representations of codeplugs and
  related archives, including versioning and migration between them.
- **Transport** — how a computer talks to a radio: cables, serial and USB
  adapters, session setup, framing, error handling, and recovery from an
  interrupted session.
- **Validation** — checking a configuration for internal consistency and for
  compatibility with a specific model and firmware before it is written.
- **Tuning and alignment** — the calibration data a service technician reads
  and writes on a bench.
- **Depot operations** — the service-center workflows that go beyond ordinary
  CPS use, performed on equipment the operator is authorized to service.
- **Round-tripping** — reading a radio, representing it losslessly, and
  writing it back without unintended changes.

### Software

- `OpenDepotCore` — the engine and its public API.
- `OpenDepot` — desktop GUI, then web and Android frontends that reuse the
  core.

## Out of scope

- Distributing Motorola software, firmware, updates, or entitlement material.
- Providing or generating license keys, flashkeys, or feature enablement
  material.
- Operating, monitoring, or interfering with radio systems.
- Programming radios you do not own or are not authorized to service.
- Anything that requires material obtained in violation of law or contract.
- Voice codec implementations that would require patented technology we
  cannot license; those stay outside the core and are not a project goal.

## Adjacent but separate

- Cable and adapter hardware design. Useful, but a different repository if it
  happens.
- Radio repair, component-level troubleshooting, and test equipment.
- P25 infrastructure. The project programs subscriber equipment; it does not
  implement a system.

## How scope changes

Scope changes by pull request to this file, with a short rationale. If a
proposed feature sits on a legal or ethical boundary, it needs maintainer
sign-off before code is written, not after.
