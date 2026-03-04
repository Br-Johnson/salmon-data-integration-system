# Deep Research Context Pack

## Project

**Title (working):** Salmon Data Integration System (SDIS)

**Target venue:** Nature Scientific Data

**Target format:** **Article** (not Data Descriptor)

**Why this format:** This manuscript describes a standards/workflow/ontology system for data sharing infrastructure, not a single dataset release paper.

---

## Objective for this Deep Research run

Produce a citation-rich evidence base and editorial recommendations that can convert the current draft into a submission-ready Scientific Data **Article**.

The run should focus on:

1. Scientific grounding of architecture and workflow claims.
2. Strong comparative context against related standards/workflow papers.
3. Journal-fit and structure optimization for Scientific Data Article expectations.
4. High-quality citations with traceable evidence and no hallucinated references.

---

## Current manuscript status

Draft file:
- `manuscript/nature-scientific-data-data-descriptor-draft.md`

Current branch:
- `paper/nature-scientific-data-whitepaper`

Current framing:
- Introduction
- System design principles
- Architecture
- Workflow implementation
- Methods/quality controls
- Outputs/reuse pathways
- Limitations
- Discussion
- Data Availability / Code Availability

---

## Core system components to represent accurately

1. **DFO salmon ontology**
   - https://github.com/dfo-pacific-science/dfo-salmon-ontology

2. **Salmon domain ontology**
   - https://github.com/salmon-data-mobilization/salmon-domain-ontology

3. **Salmon ontology hub/docs**
   - https://github.com/salmon-data-mobilization/salmon-ontology-hub

4. **Salmon Data Package specification**
   - https://github.com/dfo-pacific-science/smn-data-pkg

5. **metasalmon R package**
   - https://github.com/dfo-pacific-science/metasalmon

6. **Salmon Data Standardizer GPT app (human-supervised mapping aid)**
   - https://chatgpt.com/g/g-69375eab4f608191863e8c23313a6f9f-salmon-data-standardizer

---

## Non-negotiable framing constraints

- Treat the GPT app as a **decision-support accelerator**, not an autonomous authority.
- Keep strong **human-in-the-loop** governance language for semantic mapping decisions.
- Avoid unsupported performance claims.
- Avoid promotional language (novel, groundbreaking, first-of-its-kind unless evidence explicitly supports it).
- Maintain compatibility with Scientific Data editorial style.

---

## Priority research questions

### A) Journal fit and structure

1. What recent Scientific Data **Article** papers (not Data Descriptors) discuss standards, ontologies, workflows, or data sharing infrastructure?
2. What section patterns are common in accepted Scientific Data Articles of this type?
3. What tone and claim style is most consistent with successful papers in this category?

### B) Standards and semantic interoperability evidence

4. What literature best supports ontology-mediated data interoperability in ecology/fisheries/environmental data systems?
5. What evidence supports layered ontology governance (shared domain + organization-specific operational ontology)?
6. What references best justify explicit mapping artifacts and traceability for reproducible data integration?

### C) Packaging and validation evidence

7. What evidence supports formal data packaging standards for reuse and machine-actionable exchange?
8. What quality-control and validation frameworks are considered robust in comparable systems?
9. What are accepted best practices for reproducible validation release gates and versioned artifacts?

### D) Responsible AI-assisted standardization

10. What peer-reviewed evidence supports AI-assisted schema/metadata harmonization with expert review?
11. What failure modes are commonly reported, and what governance controls are recommended?
12. What citation-backed language can safely describe benefits while avoiding overclaim?

### E) FAIR and CARE positioning

13. How should FAIR principles be operationalized in systems like SDIS?
14. How should CARE-aligned governance considerations be acknowledged for Indigenous data contexts in environmental/fisheries settings?

### F) Comparative positioning

15. What related systems are most comparable (architecture and objective), and what differentiates SDIS?
16. Where does SDIS provide incremental value relative to existing standards ecosystems?

---

## Evidence quality requirements

- Prefer peer-reviewed sources, official standards docs, and durable institutional references.
- Prioritize 2016–present for implementation guidance, while including foundational earlier work when necessary.
- Include DOI/PMID/arXiv wherever available.
- Include direct quote snippets (<=25 words) with section/page location for claims that will anchor manuscript changes.
- Flag uncertain evidence explicitly.
- Do not invent references.

---

## Required Deep Research outputs

1. **Annotated bibliography** (high-confidence sources only)
   - grouped by manuscript section (Introduction, Methods, Discussion, etc.)

2. **Scientific Data fit brief**
   - article-type precedent examples
   - recommended final section structure
   - title/abstract language recommendations

3. **Claim-evidence matrix**
   - Claim ID
   - current wording
   - risk type (overclaim/underspecified/missing citation)
   - recommended revised wording
   - supporting citation(s)

4. **Section-by-section gap analysis**
   - what is missing
   - where to insert supporting evidence
   - what to remove or soften

5. **Rewrite recommendations**
   - revised abstract
   - revised introduction opener
   - revised discussion close
   - suggested limitations paragraph

6. **Figure/table evidence plan**
   - what each figure/table should prove
   - citations needed per figure/table

---

## Acceptance criteria for this research run

The run is successful only if it returns:

- sufficient citations to support major architecture and workflow claims,
- concrete section-level edits tied to evidence,
- a clear path to a submission-ready Scientific Data Article draft,
- and no unverifiable references.
