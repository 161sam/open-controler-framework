# ROADMAP.md

# Open Controller Framework (OCF) Roadmap

This roadmap defines the staged architecture and documentation-first evolution of OCF.

Implementation should follow the architecture, not replace it.

---

## Phase 1 – Foundations

### Goal

Establish the conceptual and structural foundation of OCF as a target-agnostic framework.

### Contents

- project definition
- architectural scope
- explicit separation of core, adapter, and tooling
- repository structure planning
- terminology alignment
- documentation baseline

### Deliverables

- README.md
- AGENTS.md
- ROADMAP.md
- architecture overview documents
- explicit OCF definition
- adapter model definition
- boundary rules for core vs adapter vs tooling

---

## Phase 2 – Schema & Types

### Goal

Define the canonical data model and schema strategy for controller systems.

### Contents

- controller model vocabulary
- components and instances
- ports and signals
- control definitions
- zones and grouping
- interaction model
- mapping abstractions
- serialization strategy
- validation strategy
- profile / preset / variant concepts

### Deliverables

- schema documentation
- type system documentation
- naming conventions
- canonical entity list
- serialization rules
- validation rules
- source-of-truth definition for model semantics

---

## Phase 3 – Layout Engine

### Goal

Define deterministic layout behavior for controller structures.

### Contents

- layout primitives
- coordinate and placement concepts
- zones and regions
- spacing and sizing rules
- component anchoring
- alignment logic
- deterministic layout resolution
- variant-aware layout handling

### Deliverables

- layout architecture document
- layout rule set
- deterministic resolution strategy
- layout terminology guide
- boundary between layout metadata and mechanical metadata

---

## Phase 4 – Constraints

### Goal

Specify the rule system that validates and constrains controller designs.

### Contents

- geometric constraints
- logical constraints
- compatibility constraints
- component dependency rules
- validation severity model
- conflict detection concepts
- constraint composition
- constraint reporting model

### Deliverables

- constraint architecture document
- constraint taxonomy
- validation and conflict model
- rules for deterministic constraint evaluation
- documentation for constraint ownership across core and adapters

---

## Phase 5 – Adapter Layer

### Goal

Define how target-specific translation is structured without polluting the core.

### Contents

- adapter contracts
- target capability model
- target compatibility validation
- translation boundaries
- export orchestration
- adapter registration concepts
- error and fallback handling
- future plugin-facing adapter strategy

### Deliverables

- adapter API design document
- adapter lifecycle definition
- target capability model
- adapter contract rules
- clear export vs adapter distinction
- extension strategy for future targets

---

## Phase 6 – Export Targets (DAWs / MIDI / Runtime)

### Goal

Specify the first conceptual target families supported by OCF.

### Contents

- DAW target family
  - Bitwig
  - Ableton
- MIDI target family
- runtime target family
  - Giada
- network target family
  - OSC
  - future protocol targets
- artifact generation strategy
- target-specific validation expectations

### Deliverables

- target family overview
- conceptual adapter specs for each target class
- export artifact matrix
- compatibility notes
- initial target support policy
- documented assumptions and exclusions per target class

---

## Phase 7 – Integration with FreeCAD

### Goal

Define the handoff between mechanical authoring and the OCF core model.

### Contents

- FreeCAD role clarification
- authoring-to-schema handoff
- mechanical metadata boundaries
- controller logic vs CAD representation
- roundtrip considerations
- import/export expectations
- frontend independence safeguards

### Deliverables

- FreeCAD integration document
- authoring workflow specification
- schema handoff model
- roundtrip boundary definition
- explicit statement that FreeCAD is primary frontend, not exclusive source of truth

---

## Long-Term Direction

After the foundational phases, OCF should support:

- reusable component libraries
- templates and variants
- target-specific adapter packs
- ecosystem-facing tooling
- plugin-ready extension points
- multiple authoring and export workflows

The long-term objective is a clean, stable controller framework that can outlive individual tools, runtimes, and integrations.
