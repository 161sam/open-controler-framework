# AGENTS.md

## Project

Open Controller Framework (OCF)

OCF is a schema-first, target-agnostic framework for controller definition and transformation.

---

## Core Principle

OCF is the **canonical logical layer**.

Everything else is external.

---

## Non-Negotiable Rules

### 1. Core is fully independent

OCF must not depend on:

- specific authoring tools
- CAD systems
- ECAD tools
- runtimes
- DAWs
- external workflows

---

### 2. Strict separation

Always separate:

#### Core
- schema
- types
- layout
- constraints
- validation
- interaction model

#### Adapter
- target-specific logic
- translation
- export

#### Tooling
- UI
- CAD
- editors
- workflows

---

### 3. No target leakage

Core must not contain:

- DAW logic
- MIDI specifics
- protocol-specific behavior
- runtime assumptions

---

### 4. No frontend leakage

Core must not contain:

- FreeCAD logic
- KiCad logic
- STEP/PCB assumptions
- Workbench-specific behavior

---

### 5. Schema is source of truth

Never treat:

- UI state
- exported data
- adapter output

as canonical.

Only OCF schema is canonical.

---

## Decision Rules

### Belongs in Core?

YES if:

- defines controller semantics
- defines structure
- defines constraints
- defines layout rules

---

### Belongs in Adapter?

YES if:

- target-specific
- export-related
- constrained by external system

---

### Belongs in Tooling?

YES if:

- UI-related
- CAD-related
- workflow-related
- visualization-related

---

## What Agents May Do

- refine architecture
- improve documentation
- clarify boundaries
- define schemas
- define constraints
- define layout rules
- define adapter contracts

---

## What Agents Must NOT Do

- add target logic to core
- add CAD logic to core
- optimize for one system
- bypass schemas
- mix layers

---

## Design Priority

1. correctness
2. clarity
3. portability
4. extensibility

NOT:

- convenience
- shortcuts
- early optimization

---

## Final Rule

If something makes OCF depend on a tool, a runtime, or a target:

→ it is wrong
