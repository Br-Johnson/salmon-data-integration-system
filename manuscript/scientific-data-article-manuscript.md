# A standards-driven workflow architecture for interoperable salmon data sharing

Brett Johnson1*

1 think|thunk, Chilliwack, British Columbia, Canada  
*Correspondence: brett@thinkthunk.io

## Abstract

Salmon monitoring data are produced across programs that differ in schema design, variable definitions and packaging practices. This heterogeneity can impede interoperability and reduce downstream reuse. We describe the Salmon Data Integration System (SDIS), a standards-driven workflow that couples layered ontology governance, a formal data packaging specification, release-gated validation and auditable mapping records. SDIS links a shared salmon domain ontology with an organization-specific operational ontology, expresses exchange-ready outputs through the Salmon Data Package specification, and uses validation tooling to check structural and semantic consistency before release. The workflow includes an AI-assisted mapping interface used to generate candidate mappings and draft field descriptions; expert review and validation are required for all final mappings. The contribution is an implementable architecture for converting heterogeneous source tables into semantically aligned, exchange-ready data products with explicit decision traceability. This Article focuses on mechanics of data sharing rather than hypothesis-testing biology.

## Introduction

Open ecological data sharing has expanded substantially, but interoperability remains constrained by heterogeneous structures, inconsistent metadata practices and diverging semantic assumptions across data-producing groups [4,6,7]. In salmon data systems specifically, representational decisions in ontology and data-model design can alter interpretation and downstream inference, underscoring that integration is a governance and methodology problem, not only a file-format problem [5].

Scientific Data Articles explicitly cover standards, ontologies, workflows and other data-sharing infrastructure, and are not intended to present hypothesis-testing biological findings [1,2]. SDIS is therefore presented as a technically oriented architecture for data sharing mechanics, rather than a Data Descriptor for a single deposited dataset [1,2].

The objective of SDIS is to support FAIR-aligned interoperability by making semantic choices explicit, packaging structure reproducible and validation outputs reviewable [4].

## System scope and contribution

SDIS defines a coordinated integration workflow with five coupled components:

1. **A shared semantic layer** for cross-context domain concepts.
2. **An operational semantic layer** for organization-specific policy and implementation semantics.
3. **A formal data package specification** for exchange-ready releases.
4. **Release-gated validation** (structural and semantic checks).
5. **Mapping and provenance artefacts** that preserve traceability from source fields to release outputs.

The primary contribution is a reusable architecture and governance pattern for producing exchange-ready salmon data products with explicit, inspectable semantic alignment.

## Architecture

### Semantic layers

The architecture separates shared domain semantics from organization-specific operational semantics. Shared concepts are maintained in the salmon domain ontology, while policy- and operations-specific concepts are maintained in the DFO salmon ontology. This layered approach is intended to preserve cross-context interoperability while allowing local precision where required [5].

- Shared semantic layer: `salmon-domain-ontology`
- Operational semantic layer: `dfo-salmon-ontology`

### Packaging layer

SDIS operationalizes data exchange using the Salmon Data Package (SDP) specification (`smn-data-pkg`). Conceptually, this aligns with broader packaging patterns that pair machine-readable metadata with declared resources and explicit structure [8-10]. SDIS uses a salmon-focused package specification to support consistent table/field documentation and validation expectations for the monitoring domain, while remaining compatible with general packaging principles.

### Validation layer

Validation is treated as a release gate, not a post hoc check. Structural constraints are assessed against package rules; semantic consistency is assessed through identifier resolution and mapping coherence. Where graph-oriented constraints are used, SHACL-compatible validation patterns are applicable [11]. Mapping and transformation traceability can be represented using provenance-compatible artefacts [12].

### AI-assisted mapping interface

SDIS includes the Salmon Data Standardizer GPT app as a candidate-generation layer for field mappings and semantic alignment proposals. This stage is explicitly advisory. All final mappings require expert review and downstream validation before release. This bounded role is consistent with evidence that LLM-assisted schema matching can be useful but is context-sensitive and error-prone without verification [14], and with Scientific Data policy requiring disclosure of AI use and human accountability [3].

## Methods

### Workflow stages

SDIS follows six stages:

1. **Source profiling:** characterize source tables, fields, units and provenance context.
2. **Semantic alignment:** identify entities/properties and align to shared and operational ontologies.
3. **Candidate mapping generation:** produce draft mappings (manual and AI-assisted) for review.
4. **SDP package construction:** materialize standardized package metadata and resources.
5. **Validation and remediation:** run structural/semantic checks and resolve blocking issues.
6. **Release and integration:** publish versioned artefacts for downstream exchange and reuse.

This staged process reflects established schema-matching and data-integration practice, where automated matching and expert review are combined to reduce mapping error [13].

### Validation gates and evidence outputs

A release candidate is considered technically ready when:

- required package structures and metadata are complete,
- ontology identifier bindings resolve and pass semantic checks,
- mapping decisions are reviewed and recorded,
- validation reports are retained with release materials.

Minimum evidence outputs include:

- mapping crosswalk tables,
- validation logs/reports,
- release notes and version identifiers,
- provenance notes linking source assumptions to package outputs.

### Reproducibility controls

Each release should record the specific versions of standards, ontologies and tooling used for package generation and validation. Reproducibility requires enough operational detail to re-run checks in a clean environment [15].

### Governance, accountability and AI use disclosure

Semantic ambiguities and policy-sensitive mappings require explicit human sign-off. AI-assisted suggestions are never treated as authoritative outputs. This governance posture is intended to reduce automation-related error propagation while preserving efficiency in candidate generation [3,5,14].

In SDIS implementations, an LLM-based interface (Salmon Data Standardizer GPT) may be used during candidate mapping generation to draft candidate alignments and field descriptions. These outputs are treated as non-authoritative suggestions. Final mapping decisions remain the responsibility of human curators and are accepted only after review and validation.

Where datasets intersect Indigenous rights, interests or sensitive community contexts, SDIS implementations should apply governance consistent with CARE-aligned principles and applicable local protocols [16,17].

## Implementation outputs and reuse pathways

### Core outputs

SDIS produces four release classes:

1. ontology-aligned mapping artefacts,
2. SDP-conformant data packages,
3. validation artefacts,
4. versioned release metadata.

### Intended reuse pathways

The architecture is intended to support:

- cross-program harmonization,
- inter-agency exchange,
- more consistent downstream analytical inputs,
- audit-ready curation and revision cycles.

Claims about reduced effort should be interpreted as design intent until quantified through formal implementation studies.

### Relation to comparable Scientific Data Articles

Recent Scientific Data Articles on ontologies, workflow registries and data standards show a consistent pattern: one clear infrastructural contribution, explicit implementation artefacts, and bounded claims tied to demonstrated outputs [18-23]. SDIS follows this contribution model.

## Limitations

SDIS does not eliminate the need for sustained expert curation. Ontologies, mappings and package constraints evolve; maintenance and review capacity remain limiting factors. The workflow also cannot correct severe upstream quality defects such as missing variables, inconsistent measurement protocols or persistent misclassification [5].

AI-assisted mapping provides candidate acceleration but may produce plausible yet incorrect alignments. Performance is sensitive to context quality, and over- or under-specification can degrade output reliability [14]. For that reason, SDIS requires human approval and validation before release [3].

## Discussion

SDIS is presented as a standards-driven sharing architecture for salmon data stewardship. The contribution is methodological and infrastructural: a reproducible pathway from heterogeneous source structures to semantically documented, exchange-ready outputs. This aligns with Scientific Data’s Article scope for standards, ontologies, workflows and other mechanics of data sharing [1,2].

Future evaluation should quantify operational outcomes (for example, mapping stability across releases, validation pass/fail profiles, and integration effort across partner contexts). Until those measurements are reported, impact claims should remain conservative and evidence-bounded.

## Data Availability

This Article describes non-code data-sharing infrastructure outputs, including ontologies, package specifications and workflow artefacts.

Public resources described in this manuscript:

- DFO salmon ontology (ontology release files, for example OWL/Turtle): <https://github.com/dfo-pacific-science/dfo-salmon-ontology>
- Salmon domain ontology (ontology release files, for example OWL/Turtle): <https://github.com/salmon-data-mobilization/salmon-domain-ontology>
- Salmon ontology hub/docs: <https://github.com/salmon-data-mobilization/salmon-ontology-hub>
- Salmon Data Package specification (schema/specification artefacts): <https://github.com/dfo-pacific-science/smn-data-pkg>
- SDIS integration repository (manuscript + integration documentation): <https://github.com/Br-Johnson/salmon-data-integration-system>

At submission, this section should additionally cite a versioned release snapshot (with a persistent identifier such as a DOI) containing the specific ontology versions, SDP specification version, and any mapping/validation artefacts referenced in the manuscript.

## Code Availability

Software resources used in the SDIS workflow include:

- `metasalmon` R package: <https://github.com/dfo-pacific-science/metasalmon>
- Salmon Data Standardizer GPT app (candidate mapping support interface): <https://chatgpt.com/g/g-69375eab4f608191863e8c23313a6f9f-salmon-data-standardizer>

No new standalone software package is introduced in this manuscript. Reproducibility relies on versioned releases of the repositories listed above and documented validation procedures.

## References

1. Scientific Data. Aims and scope. <https://www.nature.com/sdata/aims-and-scope> (accessed 2026-03-04).
2. Scientific Data. Submission guidelines. <https://www.nature.com/sdata/submission-guidelines> (accessed 2026-03-04).
3. Scientific Data. AI policy. <https://www.nature.com/sdata/policies/ai> (accessed 2026-03-04).
4. Wilkinson, M. D. *et al.* The FAIR Guiding Principles for scientific data management and stewardship. **Sci. Data** **3**, 160018 (2016). https://doi.org/10.1038/sdata.2016.18
5. Katz, S. L. *et al.* Data system design alters meaning in ecological data: salmon habitat restoration across the U.S. Pacific Northwest. **Ecosphere** **10**, e02920 (2019). https://doi.org/10.1002/ecs2.2920
6. Reichman, O. J., Jones, M. B. & Schildhauer, M. P. Challenges and opportunities of open data in ecology. **Science** **331**, 703-705 (2011). https://doi.org/10.1126/science.1197962
7. Michener, W. K. Ecological data sharing. **Ecol. Inform.** **29**, 33-44 (2015). https://doi.org/10.1016/j.ecoinf.2015.06.010
8. Frictionless Data. Data Package specification v1. <https://specs.frictionlessdata.io/data-package/> (accessed 2026-03-04).
9. Soiland-Reyes, S. *et al.* Packaging research artefacts with RO-Crate. **Data Sci.** **5**, 97-138 (2022). https://doi.org/10.3233/DS-210053
10. Kunze, J. *et al.* The BagIt file packaging format (V1.0). RFC 8493 (2018). <https://www.rfc-editor.org/rfc/rfc8493.html>
11. W3C. Shapes Constraint Language (SHACL). <https://www.w3.org/TR/shacl/> (accessed 2026-03-04).
12. W3C. PROV-O: The PROV Ontology. <https://www.w3.org/TR/prov-o/> (accessed 2026-03-04).
13. Rahm, E. & Bernstein, P. A. A survey of approaches to automatic schema matching. **VLDB J.** **10**, 334-350 (2001). https://doi.org/10.1007/s007780100057
14. Parciak, M. *et al.* Schema Matching with Large Language Models: an Experimental Study. arXiv (2024). https://doi.org/10.48550/arXiv.2407.11852
15. Sandve, G. K., Nekrutenko, A., Taylor, J. & Hovig, E. Ten Simple Rules for Reproducible Computational Research. **PLoS Comput. Biol.** **9**, e1003285 (2013). https://doi.org/10.1371/journal.pcbi.1003285
16. Carroll, S. R. *et al.* The CARE Principles for Indigenous Data Governance. **Data Sci. J.** **19**, 43 (2020). https://doi.org/10.5334/dsj-2020-043
17. Carroll, S. R. *et al.* Operationalizing the CARE and FAIR Principles for Indigenous data futures. **Sci. Data** **8**, 108 (2021). https://doi.org/10.1038/s41597-021-00892-0
18. Gustafsson, O. J. R. *et al.* WorkflowHub: a registry for computational workflows. **Sci. Data** **12**, 837 (2025). https://doi.org/10.1038/s41597-025-04786-3
19. Schwantes, C. J. *et al.* A minimum data standard for wildlife disease research and surveillance. **Sci. Data** **12**, 1054 (2025). https://doi.org/10.1038/s41597-025-05332-x
20. Köhler, C. A. *et al.* Improving data sharing and knowledge transfer via the Neuroelectrophysiology Analysis Ontology (NEAO). **Sci. Data** **12**, 907 (2025). https://doi.org/10.1038/s41597-025-05213-3
21. Magland, J. F. *et al.* Facilitating analysis of open neurophysiology data on the DANDI Archive using large language model tools. **Sci. Data** **12**, 1988 (2025). https://doi.org/10.1038/s41597-025-06285-x
22. Bottomly, D. *et al.* Biomedical Data Manifest: A lightweight data documentation mapping to increase transparency for AI/ML. **Sci. Data** (2026). https://doi.org/10.1038/s41597-026-06670-0
23. Mauer, K. *et al.* Semantic alignment of the German Human Genome-Phenome Archive metadata model in Europe’s genomics field. **Sci. Data** **13**, 242 (2026). https://doi.org/10.1038/s41597-026-06575-y

## Author Contributions

B.J. conceived the manuscript, designed the SDIS architecture description, synthesized sources, and wrote the manuscript.

## Competing Interests

The author declares no competing interests.

## Funding

No dedicated external funding was received for preparation of this manuscript.

## Acknowledgements

The author thanks collaborators in salmon data standards and ontology development communities for ongoing discussion and feedback.

## Ethics statement

Not applicable. This manuscript describes data standards and workflow infrastructure and does not report studies involving human participants or animals.
