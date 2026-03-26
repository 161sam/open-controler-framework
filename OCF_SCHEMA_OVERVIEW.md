
# OCF_SCHEMA_OVERVIEW.md

# Open Controller Framework – Schema Overview

This document defines the **conceptual data model** of OCF.

It answers:

- What is a controller in OCF?
- What entities exist?
- How are they related?
- What is part of the canonical model?

This is a **conceptual specification**, not an implementation.

---

## 1. Core Principle

OCF is **schema-first**.

The schema defines:

- structure
- semantics
- relationships
- constraints

Everything else (UI, CAD, targets) depends on this model.

---

## 2. High-Level Model

A controller is composed of:

```

Controller
├── Components
├── Controls
├── Layout
├── Constraints
├── Interactions
├── Mappings
└── Metadata

```

---

## 3. Core Entities

### 3.1 Controller

The root entity.

Represents a complete controller definition.

#### Responsibilities

- defines scope
- contains all elements
- acts as entry point

#### Contains

- components
- controls
- layout
- constraints
- interactions
- mappings
- metadata

---

### 3.2 Components

Reusable building blocks.

Examples:

- knob
- fader
- button
- encoder
- display
- pad

#### Characteristics

- typed
- reusable
- parameterizable

#### Purpose

- define *what exists physically/logically*

---

### 3.3 Controls

Instances of components.

#### Responsibilities

- reference a component
- define identity within controller
- hold instance-specific parameters

#### Example

- Component: `knob`
- Control: `filter_cutoff_knob`

---

### 3.4 Layout

Defines spatial organization.

#### Responsibilities

- positioning
- grouping
- alignment
- structure

#### Concepts

- coordinates
- regions/zones
- relative placement
- layout rules

#### Important

Layout is:

- deterministic
- independent from rendering
- independent from CAD

---

### 3.5 Constraints

Rules that validate or restrict the model.

#### Types

- geometric constraints
- logical constraints
- dependency constraints
- compatibility constraints

#### Purpose

- ensure validity
- detect conflicts
- guide layout resolution

---

### 3.6 Interactions

Abstract behavior definitions.

#### Examples

- press
- rotate
- toggle
- hold
- gesture

#### Important

Interactions are:

- abstract
- not target-specific
- not bound to MIDI or DAW APIs

---

### 3.7 Mappings

Bind interactions to semantic outcomes.

#### Purpose

- connect controls to meaning
- define intent

#### Examples

- "this knob controls filter cutoff"
- "this button triggers clip"

#### Important

Mappings are:

- abstract
- not tied to specific targets
- later resolved by adapters

---

### 3.8 Metadata

Additional information.

#### Examples

- name
- version
- author
- tags
- categories

---

## 4. Relationships

### Component → Control

- components define type
- controls are instances

---

### Control → Layout

- controls are placed in layout
- layout references controls

---

### Control → Interaction

- controls define possible interactions

---

### Interaction → Mapping

- interactions are mapped to meaning

---

### Constraints → Everything

- constraints apply globally or locally

---

## 5. Separation of Concerns

### Physical vs Logical

| Concept | Layer |
|--------|------|
| Components | physical/logical |
| Controls | logical |
| Layout | spatial |
| Constraints | validation |
| Interactions | behavior |
| Mappings | semantic |

---

### Important Rule

No concept should mix:

- layout + mapping
- interaction + target logic
- constraints + rendering

---

## 6. Abstraction Levels

OCF operates on three levels:

### 1. Structural

- components
- controls

---

### 2. Spatial

- layout
- positioning
- grouping

---

### 3. Behavioral

- interactions
- mappings

---

Constraints apply across all levels.

---

## 7. Determinism

OCF must be deterministic.

This means:

- same input → same output
- no hidden state
- no UI-dependent behavior
- no randomness in layout resolution

---

## 8. Extensibility

The schema must support:

- new component types
- new interaction types
- new mapping strategies
- new constraint types
- future adapter requirements

Without breaking existing definitions.

---

## 9. What is NOT in the Schema

The schema does NOT include:

- CAD geometry
- PCB data
- rendering instructions
- UI definitions
- DAW APIs
- MIDI specifics
- protocol formats

---

## 10. Schema Boundary

Everything entering OCF must:

- conform to schema
- be validated
- be normalized

Everything leaving OCF:

- is processed by adapters

---

## 11. Example Mental Model

Think of OCF as:

- not a tool
- not a runtime
- not a UI

But as:

→ a **language for describing controllers**

---

## 12. Summary

OCF defines:

- what a controller is
- how it is structured
- how it behaves
- how it is validated

OCF does NOT define:

- how it looks
- how it is edited
- how it is executed

---

## Next Steps

This document is the foundation for:

- schema specification
- type system (Rust)
- layout engine
- constraint system
- adapter contracts
