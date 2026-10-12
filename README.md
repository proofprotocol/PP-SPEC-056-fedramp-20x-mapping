# PP-SPEC-056: Proof of Efficacy Mapping to FedRAMP 20x

**Status:** DRAFT v0.1  
**Author:** Craig Ellrod / Nebulonium, Inc. / HACKERverse®  
**License:** Greater Good Commercial License 1.0 (GGL-C-1.0); text CC BY 4.0 under Part S. See LICENSE.md.

**Normative specification:** [`PP-SPEC-056-FedRAMP-20x-Mapping.md`](./PP-SPEC-056-FedRAMP-20x-Mapping.md)

## Purpose

This repository defines a Proof Protocol mapping between FedRAMP 20x Key Security Indicators and certification rules under the FedRAMP Consolidated Rules for 2026 (CR26) and Proof Protocol evidence, efficacy, and proof semantics.

The external framework supplies context describing what may be tested or examined. Proof Protocol remains framework-agnostic and independently establishes whether a selected control performed as claimed. Non-empirical requirements remain distinct from empirically tested efficacy results.

A Proof Protocol result is not a FedRAMP Certification, authorization, or assessment and does not establish that any cloud service offering meets FedRAMP requirements.

## Repository contents

- `PP-SPEC-056-FedRAMP-20x-Mapping.md`: normative mapping specification
- `README.md`: repository overview
- `LICENSE`: license for original Proof Protocol material
- `CONTRIBUTING.md`: contribution guidance
- `CITATION.cff`: citation metadata

## Architectural principle

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks identify what may be tested. Proof Protocol independently establishes whether a control worked and what evidence proves the result.

## Ownership and external-framework notice

This Proof Protocol mapping is independently authored. External names, identifiers, trademarks, standards text, legal text, and upstream materials remain subject to their applicable ownership and licensing. Mapping establishes interoperability, not dependency, endorsement, certification, or transfer of ownership.

"The FedRAMP name and the FedRAMP logo are the property of the General Services Administration (GSA)." (https://www.fedramp.gov/disclaimers). This repository uses the FedRAMP name only to identify the external program, does not use the FedRAMP logo, and does not claim FedRAMP Certification or government endorsement.
