
# ARCHITECTURE.md

# Open Controller Framework (OCF) – System Architecture

This document describes the architecture of the broader system around OCF.

It defines:

- system layers
- responsibilities
- data flow
- boundaries
- integration rules

OCF is the **core of this architecture**, but not the entire system.

---

## 1. Overview

The system is composed of multiple independent layers:

```

External Tools / Inputs
↓
Authoring Layer (FreeCAD + integrations)
↓
OCF Schema Boundary
↓
OCF Core (this repository)
↓
Adapter Layer
↓
Target Systems

```

Each layer has a clearly defined responsibility.

---

## 2. Layer Model

### 2.1 External Tools Layer

This layer contains tools that are **not part of the OCF system**, but may be used in the workflow.

Examples:

- KiCad (PCB design)
- STEP / CAD sources
- external libraries
- ECAD/MCAD integration tools (e.g. kicadStepUpMod)

### Role

- provide data
- support workflows
- assist authoring

### Important

These tools:

- are optional
- are replaceable
- must not define OCF semantics

---

### 2.2 Authoring Layer (OpenControllerFreeCAD)

This layer is responsible for **creating and editing controller designs**.

Primary environment:

- FreeCAD

Responsibilities:

- mechanical design (panels, enclosures)
- spatial layout (positions, spacing)
- component placement
- integration with ECAD/MCAD tools
- preparation of structured controller data

### Integration Example

```

KiCad → kicadStepUpMod → FreeCAD

```

### Output

The authoring layer produces:

- structured data (JSON / YAML / similar)
- aligned with OCF schema concepts

### Important

The authoring layer:

- is NOT the source of truth
- must not redefine core semantics
- must not introduce target-specific logic

---

### 2.3 OCF Schema Boundary

This is the most important boundary in the system.

It defines:

- what data enters OCF
- what structure is required
- what is considered valid

### Responsibilities

- normalize incoming data
- validate structure
- enforce schema constraints

### Key Principle

Everything inside OCF must be:

- deterministic
- portable
- tool-independent

---

### 2.4 OCF Core (This Repository)

OCF Core is the **canonical logic layer**.

It defines:

### Core Responsibilities

- controller data model
- type system
- layout model
- constraint system
- interaction model (abstract)
- mapping abstractions
- validation rules
- transformation logic
- adapter boundaries

### What OCF Must NOT Do

OCF must not:

- depend on FreeCAD
- depend on KiCad
- depend on external tools
- include UI logic
- include runtime logic
- include target-specific logic

---

### 2.5 Adapter Layer

Adapters translate OCF data into target-specific formats.

### Responsibilities

- interpret OCF model
- apply target constraints
- transform into target-compatible structures
- generate artifacts

### Examples of Target Classes

- DAW integrations
- MIDI mappings
- network/protocol systems
- script/config outputs

### Important

Adapters:

- depend on targets
- must not affect core semantics
- must remain isolated from OCF core logic

---

### 2.6 Target Layer

Targets consume adapter outputs.

Examples:

- DAWs
- MIDI devices
- protocol endpoints
- runtime systems
- external applications

### Role

- execution
- interpretation
- interaction

---

## 3. Data Flow

### Standard Flow

```

External Tool
↓
Authoring (FreeCAD)
↓
Structured Schema
↓
OCF Core
↓
Adapter
↓
Target

```

---

### Example Flow (PCB + Controller)

```

KiCad
↓
kicadStepUpMod
↓
FreeCAD (OpenControllerFreeCAD)
↓
OCF Schema
↓
OCF Core
↓
Adapter
↓
Target System

```

---

## 4. Separation of Concerns

### Mechanical vs Logical vs Target

| Layer | Responsibility |
|------|----------------|
| External Tools | ECAD / data sources |
| Authoring | mechanical + spatial design |
| OCF Core | logical model |
| Adapter | target translation |
| Target | execution |

---

## 5. Source of Truth

The **only source of truth** for controller semantics is:

→ **OCF Schema + Core Model**

Not:

- FreeCAD files
- KiCad files
- STEP files
- adapter outputs
- runtime state

---

## 6. Integration Rules

### Allowed

- Authoring layer may use external tools
- Authoring layer may import ECAD/MCAD data
- Adapters may depend on target APIs

---

### Forbidden

#### In OCF Core:

- CAD logic
- PCB logic
- UI logic
- target APIs
- external tool assumptions

---

## 7. Replaceability Principle

Each layer must be replaceable:

| Layer | Replaceable |
|------|-------------|
| External Tools | YES |
| Authoring | YES |
| OCF Core | NO (central) |
| Adapter | YES |
| Target | YES |

---

## 8. Extensibility Model

The system is designed to grow via:

- new authoring tools
- new adapters
- new target types
- new component libraries

OCF remains stable while the ecosystem evolves.

---

## 9. Design Principles

- schema-first
- strict separation of concerns
- deterministic transformations
- portability
- modularity
- independence from tools and targets

---

## 10. Summary

OCF is the **center of the system**, but not the whole system.

- Authoring tools create data
- OCF defines meaning
- Adapters translate
- Targets execute

External tools like ECAD/MCAD integrations are:

- useful
- powerful
- optional

But never part of the core.
