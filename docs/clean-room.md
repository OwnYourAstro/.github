# Clean-room process

This document describes how OwnYourAstro produces interoperable software
without copying vendor work. It applies to every repository in the
organization.

## Principle

A clean-room implementation is written from a **description** of behavior,
not from the artifact that implements it. If the person writing code has seen
the vendor's source, disassembly, or internal documentation, the result is not
clean, no matter how it was typed.

The process exists to make that boundary explicit, auditable, and boring.

## Roles

### Analyst

Works from hardware and observable behavior. Produces:

- observation records (what was done, on what, and what happened),
- behavioral specifications,
- test vectors and sample captures.

An analyst may use vendor-supplied software to *observe* behavior — for
example, to capture what a programming session sends over a cable — but may
not decompile it, extract its source, or paste its contents into a spec.

Analysts do not write product code.

### Implementer

Writes code from specifications and test vectors. An implementer may read:

- the specification,
- the test vectors,
- public standards and datasheets,
- third-party open-source code with a compatible license.

An implementer may not read vendor binaries, decompiled output, leaked
material, or NDA material for the feature they are implementing.

### Reviewer

Verifies two things independently:

1. **Spec adequacy** — the behavior is described precisely enough to
   implement, with provenance recorded.
2. **Implementation provenance** — the code traces to the spec, not to a
   vendor artifact, and contains no copied material.

A reviewer who has seen restricted material for a feature should not review
the matching implementation.

## Artifacts

| Artifact | Contains | Must not contain |
| --- | --- | --- |
| Observation record | Steps, hardware, firmware, result | Vendor code or text |
| Specification | Behavior, fields, states, errors | Copied listings |
| Test vector | Input, expected output, provenance | Third-party personal data |
| Implementation | Original source | Anything from the rows above |

## Provenance

Every behavioral claim in a spec carries a provenance tag:

- `bench` — observed on hardware the contributor owns or is authorized to
  service.
- `public` — from a publicly available document, with a citation.
- `capture` — from traffic the contributor recorded themselves.
- `inferred` — reasoned from other claims; must name them.
- `unverified` — plausible but not yet observed.

Claims tagged `unverified` must not be the sole basis for a destructive
operation such as writing to a radio.

## Contamination

If you realize you have seen restricted material relating to a feature:

1. Stop working on that feature.
2. Tell a maintainer privately.
3. The feature's specs and implementation are reviewed from scratch, and the
   affected code may be rewritten by someone who has not seen the material.

This is not a punishment. It is how the project stays defensible.

## Handling of vendor software and data

OwnYourAstro does not host, mirror, or distribute vendor software, firmware,
installers, or entitlement material. Do not attach them to issues or pull
requests. Do not commit captured traffic that embeds another party's
credentials, identifiers, or personal data.

## Scope of lawfulness

Contributors must obtain hardware, software, and documentation lawfully and
must not violate contracts or confidentiality obligations to participate. If
you are bound by an agreement that restricts what you may work on, honor it
and contribute elsewhere in the project.
