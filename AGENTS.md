# AGENTS.md

## Project

Open Controller Framework (OCF)

OCF is a modular, target-agnostic framework for defining, validating, transforming, and exporting controller systems.

This repository contains the core logical foundation of OCF.

## Primary Goal

Build a clean, reusable, schema-first controller framework that sits between authoring frontends and concrete targets.

OCF must remain:

- DAW-agnostic
- runtime-agnostic
- frontend-agnostic at the core level

## Core Architecture Rules

### 1. Keep Core, Adapter, and UI Separate

Always preserve the separation between:

- **Core**
  - canonical types
  - schemas
  - validation
  - layout logic
  - constraints
  - abstract interaction and mapping models
- **Adapter**
  - target-specific translation logic
  - target capability handling
  - export generation
- **UI / Tooling**
  - editors
  - helper tools
  - plugin management
  - visual workflows

Do not mix these concerns.

### 2. OCF Core Must Stay Target-Agnostic

The core may describe abstract controller behavior, but it must not contain:

- Bitwig-specific logic
- Ableton-specific logic
- Giada-specific runtime logic
- FreeCAD-specific UI behavior
- host-application-specific assumptions

### 3. FreeCAD Is Not the Core

FreeCAD is the primary mechanical authoring frontend, but not the logical source of truth by itself.

Do not design OCF in a way that requires FreeCAD internals for the core model to make sense.

### 4. Giada Is Not the Definition of OCF

Giada is one possible runtime target.

Do not design the core around Giada assumptions.
Do not turn OCF into a Giada-specific abstraction layer.

## Single Source of Truth

The canonical source of truth for controller semantics must be the OCF schema and type system.

Implications:

- UI data must not silently redefine schema meaning
- adapter internals must not redefine core semantics
- runtime assumptions must not back-propagate into core types
- generated artifacts are never the canonical model

## What Agents May Do

Agents may:

- refine documentation
- improve architecture clarity
- propose clearer crate/module boundaries
- strengthen schema definitions
- improve validation concepts
- specify adapter contracts
- identify inconsistencies
- restructure docs for maintainability
- make implicit architecture decisions explicit

## What Agents Must Not Do

Agents must not:

- add DAW-specific logic into the core
- add runtime-specific shortcuts into generic types
- treat FreeCAD as the only valid authoring path
- treat Giada as the primary or exclusive target
- collapse adapter and core boundaries
- invent undocumented hidden assumptions
- bypass schema definitions with ad-hoc structures
- optimize for one target in a way that harms portability

## Schema and Types

Agents must prefer:

- explicit schemas
- portable types
- deterministic transformations
- stable naming
- validation-friendly structures
- adapter-safe abstractions

When in doubt:

- move target specifics out of the core
- keep semantics abstract
- document assumptions explicitly

## Core vs Adapter Decision Rule

If logic answers the question:

- “What is a controller?”
- “What controls, layout, constraints, and interactions exist?”
- “How should portable validation work?”

then it belongs in **Core**.

If logic answers the question:

- “How does Bitwig represent this?”
- “How does Ableton consume this?”
- “How does Giada run this?”
- “How does OSC transport this?”

then it belongs in an **Adapter**.

## Non-Negotiable Rule

No DAW-specific logic in the core.

This includes:

- API field names
- script structure assumptions
- transport semantics tied to one host
- host lifecycle assumptions
- target-specific naming conventions

## Development Style

Work:

- architecture-first
- documentation-driven
- incrementally
- with low coupling
- with high reuse in mind

Prefer:

- small, explicit decisions
- stable abstractions
- clear boundaries
- future adapter extensibility

## Repository Intent

This repository should become the stable logical heart of the larger controller ecosystem.

Everything that depends on OCF should become easier to build because OCF is cleanly defined.

Not because OCF absorbs the complexity of every target.
