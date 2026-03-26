# ROADMAP.md

# Open Controller Framework (OCF)

---

## Phase 1 – Foundations

### Goal
Define architecture and boundaries.

### Deliverables
- README
- AGENTS
- ROADMAP
- OCF definition
- adapter model

---

## Phase 2 – Schema & Types

### Goal
Define canonical data model.

### Contents
- controller structure
- components
- controls
- ports
- zones
- interactions
- mappings (abstract)

### Deliverables
- schema spec
- type definitions
- validation rules

---

## Phase 3 – Layout Engine

### Goal
Deterministic layout system.

### Contents
- positioning
- grouping
- alignment
- spacing
- layout rules

---

## Phase 4 – Constraints

### Goal
Validation and rule system.

### Contents
- geometry constraints
- logical constraints
- dependencies
- conflict detection

---

## Phase 5 – Adapter Layer

### Goal
Target translation model.

### Contents
- adapter contracts
- capability model
- compatibility checks
- export orchestration

---

## Phase 6 – Target Classes

### Goal
Define supported target types.

### Target Classes
- DAW
- MIDI
- network/protocol
- script/config

---

## Phase 7 – Integration Layer (External)

### Goal
Define interaction with external tools.

### Important

This phase does NOT implement tools.

It defines:

- schema handoff
- import expectations
- independence rules

---

## Long-Term

- component libraries
- templates
- variants
- plugin ecosystem
- adapter registry
