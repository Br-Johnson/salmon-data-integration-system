# Scientific Data article draft

**Working status:** Draft v0.2 (refactored to the **Scientific Data “Article”** format)

**Target journal/article type:** Scientific Data — **Article** (data standards / ontologies / workflows / sharing infrastructure)

**Project name:** Salmon Data Integration System (SDIS)

---

## 0) Why this refactor

This manuscript was originally scaffolded as a Data Descriptor. It has been refactored toward the Scientific Data **Article** format, which is appropriate for papers focused on:

- data standards,
- ontologies,
- workflow/infrastructure design,
- mechanics of data sharing,

rather than describing one deposited dataset as the primary scientific object.

---

## 1) Candidate titles (Article style)

> Kept within Scientific Data title constraints in mind (descriptive wording, avoid marketing language).

1. **A semantic workflow architecture for interoperable salmon data sharing**
2. **An ontology aligned data packaging system for salmon monitoring workflows**
3. **A standards based integration framework for reusable salmon data products**

---

## 2) Abstract

Interoperable salmon data sharing is constrained by heterogeneous schemas, inconsistent field semantics, and uneven packaging practices across programs. We describe the Salmon Data Integration System, a standards based workflow architecture that links ontology governance, structured data packaging, and operational validation into one reproducible process. The system combines a shared salmon domain ontology, a DFO specific ontology layer, the Salmon Data Package specification, and the metasalmon R toolkit for package checks and transformation support. An AI assisted mapping interface is included as a human supervised acceleration step for field harmonization and ontology term suggestion. This article documents design objectives, component responsibilities, workflow stages, quality controls, and implementation governance. The contribution is a practical framework for moving from raw source tables to semantically aligned, machine actionable data products suitable for exchange, analysis, and long term reuse. The architecture is designed to support transparent curation decisions, versioned releases, and reproducible validation across salmon science and management contexts.

---

## 3) Introduction

### 3.1 Problem context

Salmon data integration often requires repeated manual interpretation of local schemas, ad hoc metadata assumptions, and project-specific transformation scripts that are difficult to audit or transfer. Even when data are technically available, reuse can remain low because meaning is not represented consistently across systems.

### 3.2 Scope of this article

This paper describes a system-level approach for improving interoperability and reuse through coordinated standards and operational workflow design. The central object is **the integration system itself** (not one specific dataset), making the Scientific Data **Article** format appropriate.

### 3.3 Practical objective

The objective is to reduce friction between data creation and data reuse by making semantics, package structure, and validation steps explicit and reproducible.

---

## 4) System design principles

SDIS is designed around six principles:

1. **Semantic clarity first**: concepts and relationships are represented explicitly via ontologies.
2. **Structure second**: data exchange follows a formal package specification.
3. **Validation as a release gate**: package checks are required before downstream use.
4. **Human accountability**: automated suggestions support, but do not replace, expert decisions.
5. **Traceable transformations**: mapping and normalization choices should be inspectable.
6. **Versioned reproducibility**: standards and outputs are referenced with explicit versions.

---

## 5) Architecture of the Salmon Data Integration System

### 5.1 Component overview

| Layer | Primary function | Main implementation artifacts |
|---|---|---|
| Semantic layer (shared) | Domain-wide reusable concepts and relationships | `salmon-domain-ontology` |
| Semantic layer (operational) | Organization-specific policy and operational context | `dfo-salmon-ontology` |
| Packaging layer | Standardized data exchange structure | `smn-data-pkg` |
| Validation/tooling layer | QA/QC and transformation support | `metasalmon` |
| Assisted mapping interface | Draft harmonization and term suggestion support | Salmon Data Standardizer GPT |

### 5.2 Shared semantic layer

The shared ontology layer provides reusable, domain-oriented terms intended for cross-context interoperability. It is intended to reduce duplicate modeling effort and stabilize core conceptual meaning.

Repository:
- <https://github.com/salmon-data-mobilization/salmon-domain-ontology>

Supporting hub/docs:
- <https://github.com/salmon-data-mobilization/salmon-ontology-hub>

### 5.3 Operational semantic layer

The DFO-specific layer captures policy and operational semantics required for specific governance and implementation contexts. This allows operational precision without forcing all shared domain concepts into a single context-bound vocabulary.

Repository:
- <https://github.com/dfo-pacific-science/dfo-salmon-ontology>

### 5.4 Data packaging layer

The Salmon Data Package (SDP) specification defines packaging structure, metadata expectations, and file-level conventions for exchangeable dataset products.

Repository:
- <https://github.com/dfo-pacific-science/smn-data-pkg>

### 5.5 Validation and transformation layer

`metasalmon` provides practical R-based support for package inspection, validation workflows, and transformation tasks aligned to packaging rules.

Repository:
- <https://github.com/dfo-pacific-science/metasalmon>

### 5.6 AI-assisted harmonization interface

The Salmon Data Standardizer GPT app provides a user-facing acceleration layer for drafting mappings between source fields, package fields, and ontology candidates.

App:
- <https://chatgpt.com/g/g-69375eab4f608191863e8c23313a6f9f-salmon-data-standardizer>

Its role is advisory and preparatory; final decisions remain with human curators and formal validation tooling.

---

## 6) Workflow implementation

### 6.1 Stage 1 — Source profiling and scoping

Inputs:
- source table structures,
- field definitions,
- unit descriptions,
- known constraints/provenance notes.

Output:
- initial dataset profile and harmonization scope.

### 6.2 Stage 2 — Semantic alignment

Tasks:
- identify entities, properties, and relationship needs,
- align shared terms to the domain ontology,
- align context-specific terms to the DFO ontology,
- record unresolved concept gaps for curation.

Output:
- explicit semantic mapping draft.

### 6.3 Stage 3 — AI-assisted mapping draft (human reviewed)

Tasks:
- use the GPT interface to propose field-level standardization and ontology candidates,
- compare AI suggestions against documented definitions,
- flag ambiguities and conflicts.

Control:
- no mapping proceeds to release without expert review.

Output:
- reviewed mapping candidate set.

### 6.4 Stage 4 — SDP package construction

Tasks:
- instantiate package metadata,
- populate required data files/tables,
- encode field-level metadata and units,
- apply reviewed semantic mapping rules.

Output:
- versioned SDP candidate package.

### 6.5 Stage 5 — Validation and remediation loop

Tasks:
- run package checks,
- inspect schema/metadata/semantic issues,
- remediate failing elements,
- re-run until release gate criteria pass.

Output:
- validated package + validation evidence.

### 6.6 Stage 6 — Release and integration

Tasks:
- publish versioned package artifacts,
- archive mapping/validation evidence,
- provide machine-usable links for downstream systems.

Output:
- reusable, traceable, exchange-ready data product.

---

## 7) Methods and technical soundness controls

### 7.1 Structural controls

- required package file presence checks,
- required metadata field completion checks,
- field type/format compliance checks.

### 7.2 Semantic controls

- ontology identifier resolution checks,
- mapping coherence checks (cardinality and context),
- review sign-off on ambiguous term assignments.

### 7.3 Operational controls

- reproducible command workflows,
- environment/version capture,
- release-level change logging.

### 7.4 Human-in-the-loop checkpoints

The system enforces human checkpointing where semantic judgment is required. This is specifically important for:

- concept disambiguation,
- policy-sensitive classifications,
- context-dependent mapping decisions.

### 7.5 Auditability posture

Each release should preserve the connection between:

- source input assumptions,
- mapping decisions,
- package outputs,
- validation outcomes.

This supports later review, correction, and reuse confidence.

---

## 8) System outputs and reuse pathways

### 8.1 Primary outputs

1. ontology-aligned mapping artifacts,
2. SDP-conformant data packages,
3. validation evidence,
4. versioned release metadata.

### 8.2 Reuse pathways

- **Cross-program harmonization:** reducing repeated one-off integration work.
- **Inter-agency exchange:** improving interpretability across organizations.
- **Analytical reproducibility:** enabling clearer lineage for downstream models and reports.
- **Application integration:** providing cleaner inputs for decision-support software.

### 8.3 Intended users

- data curators,
- fisheries science analysts,
- standards developers,
- system integrators,
- policy/operations teams needing transparent data handoff.

---

## 9) Limitations and boundary conditions

### 9.1 Dependence on curation capacity

Semantic quality remains dependent on expert review bandwidth and governance discipline.

### 9.2 Ontology evolution burden

As domain understanding evolves, mappings and packages require maintenance to remain aligned with current terms.

### 9.3 Upstream data quality constraints

The system can standardize structure and semantics, but cannot fully compensate for severe source-data quality issues.

### 9.4 AI assistance limitations

AI-generated suggestions can improve speed but may introduce plausible-yet-incorrect mappings if not reviewed carefully.

---

## 10) Discussion

### 10.1 Contribution type

The contribution of SDIS is infrastructural and methodological: a composable integration architecture for standards-driven salmon data sharing and reuse.

### 10.2 Why Article format fits

Unlike a Data Descriptor centered on one deposited dataset, this work describes:

- multi-component standards architecture,
- integration mechanics,
- governance and validation workflow,
- implementation guidance for reuse.

These are aligned with Scientific Data’s Article scope for standards, ontologies, workflows, and data-sharing infrastructure.

### 10.3 Near-term maturation priorities

1. formalize mapping artifact schema,
2. publish reproducible validation command set,
3. assemble worked case studies with before/after interoperability outcomes,
4. assign persistent identifiers for key released outputs.

---

## 11) Data Availability

This Article describes standards, ontologies, tooling, and workflow infrastructure for salmon data integration.

Public resources referenced in this work:

- DFO salmon ontology: <https://github.com/dfo-pacific-science/dfo-salmon-ontology>
- Salmon domain ontology: <https://github.com/salmon-data-mobilization/salmon-domain-ontology>
- Salmon ontology hub/docs: <https://github.com/salmon-data-mobilization/salmon-ontology-hub>
- Salmon Data Package specification: <https://github.com/dfo-pacific-science/smn-data-pkg>
- SDIS integration repository: <https://github.com/Br-Johnson/salmon-data-integration-system>

`[If a specific demonstration dataset or release archive is added for submission, include repository URL, accession/DOI, file-level description, and version here.]`

---

## 12) Code Availability

Software and implementation resources:

- metasalmon R package: <https://github.com/dfo-pacific-science/metasalmon>
- Salmon Data Standardizer GPT app interface: <https://chatgpt.com/g/g-69375eab4f608191863e8c23313a6f9f-salmon-data-standardizer>

`[Add exact version pins / commit hashes / runtime environment details before submission.]`

---

## 13) References seed list (to formalize)

1. DFO Pacific Science. dfo-salmon-ontology. GitHub repository.
2. Salmon Data Mobilization. salmon-domain-ontology. GitHub repository.
3. Salmon Data Mobilization. salmon-ontology-hub. GitHub repository.
4. DFO Pacific Science. smn-data-pkg. GitHub repository.
5. DFO Pacific Science. metasalmon. GitHub repository.
6. Wilkinson, M. D. et al. The FAIR Guiding Principles for scientific data management and stewardship. Sci Data 3, 160018 (2016).

---

## 14) Figure and table plan (Article-oriented)

### Figure plan

- **Figure 1:** SDIS architecture and component boundaries.
- **Figure 2:** End-to-end workflow from source schema to validated package release.
- **Figure 3:** Governance and quality gate checkpoints.
- **Figure 4:** Example mapping traceability chain (source field → ontology term → package field).

### Table plan

- **Table 1:** Component responsibilities and interfaces.
- **Table 2:** Workflow stage inputs, outputs, and decision gates.
- **Table 3:** Validation controls (structural, semantic, operational).
- **Table 4:** Reuse pathways and target user groups.

---

## 15) Scientific Data Article readiness checklist

### Format alignment

- [x] Refactored to Article framing
- [x] Introduction-focused structure in place
- [x] System architecture described
- [x] Workflow and methods described
- [x] Limitations section included
- [x] Data Availability section included
- [x] Code Availability section included
- [ ] Final title selection
- [ ] Abstract final pass for journal wording

### Evidence and reproducibility

- [ ] Add concrete implementation case study details
- [ ] Add explicit version pins and environment details
- [ ] Add release artifacts and persistent identifiers where applicable
- [ ] Convert seed references to journal-style final references

### Submission metadata

- [ ] Author Contributions finalized
- [ ] Competing Interests statement finalized
- [ ] Funding statement finalized
- [ ] Acknowledgements finalized (if needed)

---

## 16) Next revision steps

1. Insert one concrete worked example with full traceability (source schema → mapping decisions → package output).
2. Add minimal quantitative process metrics (for example mapping throughput or validation failure classes) if available.
3. Tighten the abstract and introduction language against final title choice.
4. Convert references to Scientific Data/Nature style and add DOIs where available.
5. Prepare figure drafts to match the architecture and workflow narrative.
