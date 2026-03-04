# Nature Scientific Data submission draft

**Working status:** Draft v0.1 (foundation draft for iterative refinement)

**Target journal/article type:** Scientific Data — Data Descriptor

**Project codename:** Salmon Data Integration System (SDIS)

---

## 0) Candidate titles (Scientific Data constraints aware)

> Notes from current Scientific Data guidance: title should be descriptive, no colon, avoid marketing language, and be <=110 characters.

1. **A semantic data integration framework for interoperable salmon monitoring datasets**
2. **An ontology aligned data package system for reusable salmon monitoring data**
3. **Standardized salmon data exchange using ontologies data packages and validation tooling**

---

## 1) Abstract draft (<170 words target)

Reliable reuse of salmon monitoring data is constrained by heterogeneous schema design, inconsistent variable definitions, and weak interoperability between agencies and projects. We present the Salmon Data Integration System, a reproducible framework that combines two ontology layers, a formal Salmon Data Package specification, and validation tooling to standardize data packaging and exchange workflows. Shared domain semantics are represented in a community salmon domain ontology, while operational and policy specific semantics are represented in a DFO salmon ontology. Dataset level exchange is implemented through the Salmon Data Package specification, and package quality control is operationalized with metasalmon in R. The workflow also includes an AI assisted standardization step that proposes field mappings and ontology term candidates for expert review prior to final packaging. Together, these components provide a practical path from raw source tables to semantically annotated, machine actionable, and reviewable data packages. This descriptor documents system architecture, implementation workflow, expected data artifacts, validation procedures, and usage patterns to support transparent reuse across salmon science and management contexts.

Word count estimate: ~162

---

## 2) Background & Summary

### 2.1 Motivation

Salmon science programs routinely integrate data from multiple sources, including stock assessment, spawner surveys, habitat observations, environmental covariates, and management reporting systems. Across these streams, interoperability is often reduced by:

- locally defined column naming and inconsistent metadata depth
- divergent entity definitions (for example stock, population, life stage, run timing)
- mixed granularity of space and time fields
- weakly documented transformations between source and analysis-ready datasets

The consequence is high integration overhead, repeated one-off data cleaning, and reduced reproducibility.

### 2.2 Reuse objective

The objective of SDIS is to make salmon datasets easier to discover, interpret, validate, and reuse by coupling:

- **semantic consistency** (ontology alignment)
- **structural consistency** (data package schema)
- **operational consistency** (standardized validation and transformation workflow)

### 2.3 System framing

SDIS is a workflow and standards stack, not a single monolithic software package. It integrates existing and complementary components:

- DFO salmon ontology: <https://github.com/dfo-pacific-science/dfo-salmon-ontology>
- Salmon domain ontology: <https://github.com/salmon-data-mobilization/salmon-domain-ontology>
- Salmon ontology hub/docs: <https://github.com/salmon-data-mobilization/salmon-ontology-hub>
- Salmon Data Package (SDP) specification: <https://github.com/dfo-pacific-science/smn-data-pkg>
- metasalmon R package: <https://github.com/dfo-pacific-science/metasalmon>
- Salmon Data Standardizer GPT app: <https://chatgpt.com/g/g-69375eab4f608191863e8c23313a6f9f-salmon-data-standardizer>

### 2.4 Intended reuse value

This architecture is intended to support:

- cross-program data harmonization
- reproducible package generation and validation
- improved interoperability for downstream analysis pipelines and decision support tools
- clearer lineage between source fields, mapped semantic terms, and released package artifacts

---

## 3) Methods

### 3.1 Overall workflow

SDIS follows a five-stage process:

1. ontology alignment
2. AI-assisted standardization (human reviewed)
3. SDP-conformant package construction
4. package validation and transformation
5. downstream integration and reuse

### 3.2 Semantic layer design

#### 3.2.1 Shared domain layer

The shared domain ontology provides reusable, domain-general concepts relevant across salmon contexts. This layer anchors common vocabulary and relations intended for reuse across organizations and implementations.

#### 3.2.2 Operational layer

The DFO salmon ontology encodes policy and operational specifics required in DFO-oriented workflows. This layer enables context-specific representation without forcing duplication of shared concepts.

#### 3.2.3 Layer interaction

The implementation assumption for this draft is:

- shared reusable semantics are maintained in the salmon domain ontology
- DFO-specific semantics are maintained in the DFO ontology
- mappings between package metadata/fields and ontology terms are explicit and reviewable

### 3.3 AI-assisted standardization step

The Salmon Data Standardizer GPT app is used as a front-end accelerator for mapping preparation. The role of this step is constrained to assistance, not authority.

**Operational pattern:**

- user provides source table structure, field definitions, units, provenance notes, and known constraints
- the assistant proposes:
  - candidate SDP field mappings
  - candidate ontology term alignments
  - candidate normalization actions
- domain experts review all proposals before package finalization

**Governance rule:**

- no AI-proposed mapping is treated as final without expert review and downstream validation

### 3.4 Data package construction

Data are expressed as Salmon Data Packages using the specification in `smn-data-pkg`. Construction steps include:

1. define package-level metadata
2. prepare required data tables/files in specified formats
3. encode variable-level definitions and units
4. apply approved semantic mappings
5. bundle package files in a versioned, reproducible layout

### 3.5 Validation and transformation

`metasalmon` is used as the primary R-based operational tool for package QA/QC and transformation support.

Validation checks should cover at minimum:

- required file presence and schema conformance
- variable naming and metadata completeness
- controlled vocabulary / ontology mapping integrity checks
- unit consistency and parseability checks
- machine-readability of package-level metadata

### 3.6 Release process and versioning

For journal submission and durable reuse, each package release should include:

- immutable release identifier (version tag + date)
- changelog with semantic and structural deltas
- validation report for that release
- repository or archive URL and persistent identifier (DOI target)

### 3.7 Reproducibility posture

The reproducibility contract for SDIS should include:

- version-pinned ontology references
- version-pinned package specification reference
- version-pinned tooling stack (R and package versions)
- scripted validation commands
- release artifacts archived in a stable repository

---

## 4) Data Records

> This section must be finalized with concrete release artifact names, checksums, and persistent identifiers.

### 4.1 Record classes produced by SDIS

| Record class | Description | Canonical location (draft) |
|---|---|---|
| Ontology artifacts | OWL/SKOS or related semantic resources used for mapping | `dfo-salmon-ontology`, `salmon-domain-ontology` |
| Mapping artifacts | Table-level or field-level mapping documentation linking source fields to ontology terms | `[TO_BE_FINALIZED]` |
| Salmon Data Packages | Packaged datasets conforming to SDP spec | `[TO_BE_FINALIZED_REPOSITORY_AND_PATHS]` |
| Validation outputs | Validation logs/reports from package checks | `[TO_BE_FINALIZED]` |
| Transformation scripts | Optional scripts/notebooks used to produce released package artifacts | `[TO_BE_FINALIZED]` |

### 4.2 Required final Data Records details for submission

Before submission, this section should include:

- exact file inventory (filename, type, size)
- folder structure of deposited datasets
- data dictionary coverage for all non-obvious fields
- package-level metadata examples
- persistent identifiers for all deposited datasets

---

## 5) Technical Validation

### 5.1 Validation philosophy

Validation is designed to test both **structural integrity** (does it conform to package rules) and **semantic integrity** (do field meanings and term mappings remain coherent).

### 5.2 Validation dimensions

1. **Schema conformance**
   - required files and required fields present
   - field types and constraints are respected

2. **Metadata completeness**
   - package metadata fields populated to minimum required level
   - dataset provenance and version information present

3. **Semantic mapping checks**
   - mapped ontology identifiers resolve to expected terms
   - mapping cardinalities are coherent (for example one-to-many only when justified)

4. **Unit and value checks**
   - values parse according to declared types
   - units are present and normalized where applicable

5. **Reproducibility checks**
   - package can be validated from a clean environment with documented commands

### 5.3 Example validation workflow

1. run package-level validation through `metasalmon`
2. run custom integrity checks for project-specific constraints
3. review generated reports for blocking and non-blocking issues
4. remediate and re-run until release criteria pass
5. archive validation evidence alongside release artifacts

### 5.4 Release acceptance criteria (draft)

A package is release-ready when:

- no blocking schema errors remain
- no unresolved required metadata fields remain
- semantic mapping review is signed off by domain curator(s)
- validation report is attached to the release

---

## 6) Usage Notes

### 6.1 Recommended implementation order

1. model concepts and relationships
2. standardize source schema and term mappings
3. build SDP package
4. validate package
5. integrate into analytics/apps

### 6.2 Practical usage patterns

- **Program-level harmonization:** convert multiple local datasets into consistent SDP outputs for cross-program analysis
- **Data handoff:** package data releases for transfer between organizations with explicit semantic context
- **App integration:** feed validated, semantically labeled packages into downstream dashboards, models, or decision services

### 6.3 Human-in-the-loop recommendation

Use AI-assisted standardization to reduce manual mapping effort, but preserve expert review checkpoints before release. This balances speed and semantic accuracy.

### 6.4 Known limitations (to be completed)

- `[LIMITATION_1_PLACEHOLDER]`
- `[LIMITATION_2_PLACEHOLDER]`
- `[LIMITATION_3_PLACEHOLDER]`

---

## 7) Data Availability (submission-draft placeholders)

Data supporting this descriptor will be deposited in `[TARGET_REPOSITORY]` with persistent identifiers assigned at release.

- Dataset collection DOI: `[TO_BE_ASSIGNED]`
- Versioned package archive DOI(s): `[TO_BE_ASSIGNED]`
- Access conditions/licensing: `[TO_BE_DEFINED]`

---

## 8) Code Availability (submission-draft placeholders)

Core standards and tooling repositories:

- DFO salmon ontology: <https://github.com/dfo-pacific-science/dfo-salmon-ontology>
- Salmon domain ontology: <https://github.com/salmon-data-mobilization/salmon-domain-ontology>
- Salmon ontology hub/docs: <https://github.com/salmon-data-mobilization/salmon-ontology-hub>
- Salmon Data Package specification: <https://github.com/dfo-pacific-science/smn-data-pkg>
- metasalmon R package: <https://github.com/dfo-pacific-science/metasalmon>
- SDIS integration site/repo: <https://github.com/Br-Johnson/salmon-data-integration-system>

AI-assisted mapping interface:

- Salmon Data Standardizer GPT app: <https://chatgpt.com/g/g-69375eab4f608191863e8c23313a6f9f-salmon-data-standardizer>

`[ADD exact software versions, commit hashes, environment lock details prior to submission.]`

---

## 9) References seed list

> Add formal references and dataset citations in journal format during citation pass.

1. DFO Pacific Science. dfo-salmon-ontology. GitHub repository.
2. Salmon Data Mobilization. salmon-domain-ontology. GitHub repository.
3. Salmon Data Mobilization. salmon-ontology-hub. GitHub repository.
4. DFO Pacific Science. smn-data-pkg. GitHub repository.
5. DFO Pacific Science. metasalmon. GitHub repository.

---

## 10) Figures and tables plan for full submission

### Figure plan

- **Figure 1:** SDIS architecture overview (semantic layer + package layer + validation layer)
- **Figure 2:** End-to-end data standardization workflow from source table to released SDP
- **Figure 3:** Validation pipeline and decision gates
- **Figure 4:** Example mapping traceability from raw fields to ontology-linked package fields

### Table plan

- **Table 1:** Comparison of SDIS components and responsibilities
- **Table 2:** Required SDP metadata fields and semantic linkage points
- **Table 3:** Validation checks, methods, and pass/fail criteria
- **Table 4:** Released dataset/package inventory for this descriptor

---

## 11) Scientific Data compliance checklist draft

### Article structure

- [x] Title candidates drafted (constraint-aware)
- [x] Abstract drafted (~170 words target)
- [x] Background & Summary drafted
- [x] Methods drafted
- [x] Data Records scaffold drafted
- [x] Technical Validation drafted
- [x] Usage Notes drafted
- [ ] Data Availability finalized with DOI(s)
- [ ] Code Availability finalized with versions
- [ ] References converted to formal citation style

### Data and repository readiness

- [ ] Final data repository selected and confirmed against journal policy
- [ ] Public or review-accessible data package release prepared
- [ ] Machine-readable file manifest completed
- [ ] Data dictionary completed
- [ ] Persistent identifiers minted

### Validation and reproducibility readiness

- [ ] Validation scripts documented and repeatable from clean environment
- [ ] Release acceptance criteria formalized and executed
- [ ] Final validation report archived with release

---

## 12) Immediate next writing steps

1. Replace placeholders with concrete dataset artifacts and release identifiers.
2. Add formal methods detail for:
   - input dataset provenance,
   - mapping QA process,
   - exact validation command set.
3. Draft dataset inventory table with exact filenames and field-level dictionary references.
4. Add reproducibility environment details (R version, package lockfile/session info, runtime assumptions).
5. Build formal reference list and data citations in Scientific Data-compatible style.
6. Finalize title/abstract against strict character and wording constraints.

---

## 13) Editorial note

This draft is intentionally comprehensive and submission-oriented, but it is **not yet submission-ready** until concrete deposited datasets, formal data citations, and reproducibility metadata are completed.
