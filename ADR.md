
# ADR-001: Use of kicadStepUpMod as External ECAD/MCAD Integration Tool

## Status

Accepted

---

## Context

The project requires integration between:

- PCB design (KiCad)
- mechanical design (FreeCAD)
- controller authoring

Implementing a custom ECAD↔MCAD bridge would be complex and redundant.

kicadStepUpMod already provides:

- KiCad ↔ FreeCAD integration
- STEP export/import
- footprint alignment
- board geometry synchronization

---

## Decision

kicadStepUpMod will be used as:

- an **external workflow tool**
- within **OpenControllerFreeCAD**
- for **ECAD/MCAD integration**

It will NOT be:

- part of OCF
- a dependency of OCF
- a source of truth for controller logic

---

## Consequences

### Positive

- avoids reinventing ECAD/MCAD bridge
- leverages mature tooling
- accelerates hardware workflow
- improves mechanical accuracy

---

### Neutral

- adds external dependency in FreeCAD workflow
- requires user awareness of toolchain

---

### Negative / Risks

- AGPL license implications
- external project dependency
- version compatibility

---

## Boundaries

### OCF

Must NOT:

- depend on kicadStepUpMod
- import its logic
- mirror its structures

---

### OpenControllerFreeCAD

MAY:

- use kicadStepUpMod
- integrate workflows
- import/export data
- assist user workflows

---

## Architecture

```

KiCad
↓
kicadStepUpMod
↓
FreeCAD / OpenControllerFreeCAD
↓
OCF Schema
↓
OCF Core

```

---

## Rationale

Separation of concerns:

- ECAD/MCAD = solved externally
- Controller logic = solved by OCF

Avoid duplication.
Preserve independence.
