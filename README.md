# Salmon Data Integration System

This repository documents how the salmon ontology + data package tooling works together as one integration system.

## Core repositories

- **DFO salmon ontology**: https://github.com/dfo-pacific-science/dfo-salmon-ontology
- **Salmon domain ontology (shared domain model)**: https://github.com/salmon-data-mobilization/salmon-domain-ontology
- **Salmon domain ontology hub/docs**: https://github.com/salmon-data-mobilization/salmon-ontology-hub
- **Salmon Data Package (SDP) specification**: https://github.com/dfo-pacific-science/smn-data-pkg
- **`metasalmon` R package**: https://github.com/dfo-pacific-science/metasalmon

## How the system fits together

Think of this as a layered workflow:

1. **Shared domain semantics** live in `salmon-domain-ontology`.
2. **DFO-specific policy/operational semantics** live in `dfo-salmon-ontology`.
3. **Data exchange format** is defined by the SDP spec (`smn-data-pkg`).
4. **Operational data tooling in R** is provided by `metasalmon`.

In short: ontology layers define meaning, SDP defines structure, and `metasalmon` helps produce/validate/use data packages in practice.

## Quick how-to

### 1) Start with ontology terms

- Identify the concepts and relationships your dataset needs.
- Reuse shared terms from `salmon-domain-ontology` where possible.
- Use DFO terms from `dfo-salmon-ontology` for DFO-specific context.

### 2) Build a Salmon Data Package

- Follow the SDP spec in `smn-data-pkg`.
- Create package metadata and tables according to the required schema.
- Map package fields to ontology terms where appropriate.

### 3) Validate and work with packages in R

- Use `metasalmon` to inspect, validate, and transform package data.
- Resolve schema or semantic mapping issues before publishing/exchange.

### 4) Integrate downstream

- Publish/share valid SDPs.
- Use ontology mappings to support interoperability across teams, systems, and analyses.

## Suggested implementation pattern

- **Model first** (ontology alignment)
- **Package second** (SDP-compliant data product)
- **Validate third** (`metasalmon` checks)
- **Integrate fourth** (analytics, apps, services)

That order minimizes rework and keeps semantics + structure aligned from the start.
