# Salmon Data Integration System

This repository documents how the salmon ontology + data package tooling works together as one integration system.

## Start here (overview + demo)

- **System overview page**: https://br-johnson.github.io/salmon-data-integration-system/
- **Overview video (YouTube)**: https://youtu.be/B0Zqac49zng?si=VmOjbfMDMd2xW9fH
- **Source repository**: https://github.com/Br-Johnson/salmon-data-integration-system

## Core repositories and tools

- **DFO salmon ontology**: https://github.com/dfo-pacific-science/dfo-salmon-ontology
- **Salmon domain ontology (shared domain model)**: https://github.com/salmon-data-mobilization/salmon-domain-ontology
- **Salmon domain ontology hub/docs**: https://github.com/salmon-data-mobilization/salmon-ontology-hub
- **Salmon Data Package (SDP) specification**: https://github.com/dfo-pacific-science/smn-data-pkg
- **`metasalmon` R package**: https://github.com/dfo-pacific-science/metasalmon
- **Salmon Data GPT app**: https://chatgpt.com/g/g-69375eab4f608191863e8c23313a6f9f-salmon-data-standardizer

## How the system fits together

Think of this as a layered workflow:

1. **Shared domain semantics** live in `salmon-domain-ontology`.
2. **DFO-specific policy/operational semantics** live in `dfo-salmon-ontology`.
3. **Data exchange format** is defined by the SDP spec (`smn-data-pkg`).
4. **Operational data tooling in R** is provided by `metasalmon`.
5. **AI-assisted standardization workflow** is supported by the Salmon Data GPT app.

In short: ontology layers define meaning, SDP defines structure, `metasalmon` handles validation/transformation in R, and the Salmon Data GPT app helps people standardize incoming datasets into that workflow faster.

## Quick how-to

### 1) Start with ontology terms

- Identify the concepts and relationships your dataset needs.
- Reuse shared terms from `salmon-domain-ontology` where possible.
- Use DFO terms from `dfo-salmon-ontology` for DFO-specific context.

### 2) Use the Salmon Data GPT app to prepare data

- Open the GPT app and provide your dataset context (table structure, field meanings, units, source notes).
- Ask it to propose SDP-aligned field mappings and ontology term candidates.
- Use its output to produce a draft standardization plan/checklist before packaging.

### 3) Build a Salmon Data Package

- Follow the SDP spec in `smn-data-pkg`.
- Create package metadata and tables according to the required schema.
- Apply the reviewed mappings from Step 2.

### 4) Validate and work with packages in R

- Use `metasalmon` to inspect, validate, and transform package data.
- Resolve schema or semantic mapping issues before publishing/exchange.

### 5) Integrate downstream

- Publish/share valid SDPs.
- Use ontology mappings to support interoperability across teams, systems, and analyses.

## Suggested implementation pattern

- **Model first** (ontology alignment)
- **Standardize second** (GPT-assisted mapping + preparation)
- **Package third** (SDP-compliant data product)
- **Validate fourth** (`metasalmon` checks)
- **Integrate fifth** (analytics, apps, services)

That order minimizes rework and keeps semantics + structure aligned from the start.

## Important note

The GPT app is an accelerator, not the source of truth. Authoritative standards remain the ontologies + SDP spec, with final validation performed through reproducible package tooling (for example, `metasalmon`).
