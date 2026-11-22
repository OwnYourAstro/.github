# Architecture notes

Design intent for the split between the core and its frontends. This is a
starting point and is expected to change as the first specs land. Nothing here
fixes an implementation language.

## Shape

```
+---------------------+     +---------------------+     +---------------------+
|  OpenDepot desktop  |     |    OpenDepot web    |     |  OpenDepot Android  |
+----------+----------+     +----------+----------+     +----------+----------+
           |                           |                           |
           +---------------------------+---------------------------+
                                       |
                            +----------v----------+
                            |    OpenDepotCore    |
                            +----------+----------+
                                       |
                    +------------------+------------------+
                    |                  |                  |
             +------v------+    +------v------+    +------v------+
             |  Transports |    |   Formats   |    |   Hardware  |
             +-------------+    +-------------+    +-------------+
```

## OpenDepotCore

The core owns everything that is not presentation:

- the codeplug object model,
- readers and writers for each supported format,
- the transport abstraction and its implementations,
- validation and compatibility rules,
- operations, expressed as validated, auditable transactions,
- an error model that distinguishes recoverable from destructive failures.

The core should be usable headless, from tests, and from a script.

## Frontends

`OpenDepot` for desktop, and later the web and Android frontends, are clients
of the core. They add presentation, platform integration, and device
selection. They do not own format knowledge or protocol logic — if a frontend
needs to know how a field is encoded, that logic belongs in the core.

## Principles

**Read before write.** Every write path starts from a structure that was read
from the device or from a validated file, never from scratch.

**Lossless round trip.** Represent unknown or unrecognized data faithfully so
a read/write cycle does not silently drop vendor-specific fields. An
incomplete model is preferable to a lossy one.

**Explicit, reversible transactions.** A write is a transaction with a
preflight diff, a confirmation, and a post-write read-back comparison.
Interrupted sessions leave the operator with a known state and a recovery
path.

**Unknowns are visible.** Unparsed regions, unverified claims, and untested
model/firmware combinations surface in the UI and the API rather than being
silently assumed correct.

**One core, many shells.** Anything a second frontend would need is a core
concern by definition.

## Open questions

- Language and toolchain for the core.
- Interchange format for backup and diff.
- Whether the transport layer ships in-process or as a fast local service for
  browser-based frontends.
- Conformance test format shared across desktop, web, and Android.

These are decided by issue and pull request, with the reasoning recorded.
