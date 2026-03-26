
# Open Controller Framework (OCF)

Open Controller Framework (OCF) is a modular, schema-first framework for defining, validating, transforming, and exporting controller systems in a target-agnostic way.

OCF is the **logical core** of a controller ecosystem.  
It defines what a controller *is*, independent of:

- any specific DAW
- any runtime or host
- any CAD or authoring tool
- any export format

## Status

Early stage.

The project is currently focused on architecture, scope definition, and documentation before implementation.

---

## Goal

OCF enables controller systems to be:

- **portable**
- **reusable**
- **deterministic**
- **formally describable**

Instead of building controllers tied to one tool or runtime, OCF introduces a **canonical intermediate model**.

---

## Core Concept

A controller is not a device.

A controller is a structured system of:

- components
- controls
- layout
- constraints
- interactions
- mappings

OCF provides a formal representation of this system.

---

## Role in the Architecture

OCF sits between:

- **Authoring Frontends**
- **Target Systems**

```

Authoring → Schema → OCF → Adapter → Target

```

### Authoring Frontends (external)

Examples:

- CAD tools
- custom editors
- scripting tools

These tools produce structured data.

### OCF (this repository)

OCF:

- validates the model
- applies layout rules
- resolves constraints
- prepares data for targets

### Adapters

Adapters translate the OCF model into concrete targets.

### Targets

Targets consume adapter outputs:

- DAWs
- MIDI mappings
- scripts
- network protocols
- other systems

---

## Important Clarification

OCF is:

- **not tied to any authoring tool**
- **not tied to any runtime**
- **not tied to any host system**

OCF does **not**:

- depend on FreeCAD
- depend on KiCad
- depend on any ECAD/MCAD tooling
- embed target-specific logic

---

## What OCF Defines

OCF defines:

- controller schema
- types and entities
- component system
- layout model
- constraint system
- interaction model (abstract)
- mapping abstractions
- validation rules
- adapter boundaries

---

## What OCF Does NOT Define

OCF does not define:

- UI editors
- CAD workflows
- ECAD/PCB logic
- mechanical geometry tools
- DAW-specific behavior
- runtime execution engines

---

## Adapter Model

Adapters are responsible for:

- translating OCF → target
- applying target constraints
- generating artifacts

Examples of target classes:

- DAW integrations
- MIDI mappings
- network protocols
- script-based targets

Core remains target-agnostic.

---

## Workflow

Typical flow:

```

Authoring Tool
↓
Structured Schema (JSON/YAML)
↓
OCF Core
↓
Adapter
↓
Target System

```

---

## Design Principles

- schema-first
- deterministic
- modular
- reusable
- target-agnostic
- frontend-agnostic
- strict separation of concerns

---

## Vision

OCF aims to become:

- a reusable foundation for controller systems
- a standard for controller description
- a bridge between design and execution
- a base for ecosystem tools and plugins

---

## Repository Focus

This repository defines:

- the canonical model
- the transformation logic
- the validation system
- the adapter boundaries

It must remain:

- clean
- minimal
- independent
- extensible
