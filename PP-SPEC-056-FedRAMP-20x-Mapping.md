# PP-SPEC-056: Proof of Efficacy Mapping to FedRAMP 20x

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | FedRAMP 20x under the FedRAMP Consolidated Rules for 2026 (CR26), including Key Security Indicators (KSIs) |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how FedRAMP 20x Key Security Indicators, certification rules, and persistent validation expectations can be bound to Proof Protocol test cases, evidence, and efficacy results.

FedRAMP is a program of the U.S. General Services Administration (GSA). FedRAMP 20x is the program's KSI-based certification path. As confirmed at fedramp.gov on October 8, 2026, the 20x pilots are complete (Phase One, 20x Low Pilot; Phase Two, 20x Moderate Pilot) and Phase Three, Wide-scale Adoption, is active under the FedRAMP Consolidated Rules for 2026 (CR26). fedramp.gov lists a Class D (High) pilot as a future, estimated phase and states that FedRAMP will stop accepting new Rev5 Certifications on June 11, 2027.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source.

## 2. Scope

FedRAMP 20x supplies external context that can identify what should be examined or tested: KSI themes and indicators, certification classes, assurance rulesets, and the Security Decision Record. Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

This mapping covers the 20x path only. FedRAMP Rev5 certification and NIST SP 800-53 baselines are referenced only where a KSI lists related SP 800-53 controls.

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

A Proof Protocol result is **not** a FedRAMP Certification, authorization, assessment, Independent Verification and Validation outcome, or Marketplace listing, and does not establish that a cloud service offering meets FedRAMP requirements. Only FedRAMP and the applicable federal agencies make those determinations.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to FedRAMP 20x

Exact upstream identifiers and titles SHOULD be taken from the authoritative version being mapped and recorded in the ProofBundle™ where licensing permits. This specification does not redefine upstream requirements.

KSI identifiers on fedramp.gov use the format `KSI-<theme code>-<indicator code>` (for example, `KSI-IAM-APM`). Theme codes confirmed at the time of drafting are CED, CMT, CNA, IAM, INR, MLA, PIY, RPL, SCR, and SVC.

| FedRAMP 20x context | Proof Protocol treatment | Evidence |
|---|---|---|
| Consolidated Rules version (CR26) | Bind the rules release and the date retrieved from fedramp.gov or the machine-readable rules dataset to every proof record. | Requirement metadata |
| Certification class (Class A, B, C; Class D via Rev5) | Record the class targeted by the system under test as context only. Proof Protocol does not assign or imply a class. | Requirement metadata |
| KSI theme (e.g. IAM, MLA, SVC) | Group test cases by theme for reporting. A theme is context, not a verdict. | Corpus/test metadata |
| Key Security Indicator (`KSI-<theme>-<code>`) | Bind the KSI identifier to one or more reproducible test conditions where the indicator describes an observable technical behavior. | Proof record; corpus manifest |
| Optional KSIs for Class B or Class C | Record whether the KSI is required or optional for the targeted class. Optional status does not change verdict semantics. | Requirement metadata |
| Related SP 800-53 Controls listed on a KSI | Record the listed control identifiers as cross-reference context only. | Requirement metadata |
| Automated or persistent validation claims in a KSI | Exercise the condition and capture whether the automated mechanism actually operated and produced the claimed effect, separately from the mechanism's own reported status. | Execution evidence; outcome evidence |
| Assurance rulesets (AFC, CCM, IEC, IVV, SCN, VER) | Treat as procedural and reporting context. Bind only those elements that produce observable behavior (for example, whether a vulnerability was detected or a change was identified). | Proof records; non-empirical annotation |
| Security Decision Record (human-readable and JSON) | Record the asserted implementation separately from observed behavior. An SDR statement is a claim, not evidence of efficacy. | Control descriptor |
| Exception/failure condition | Exercise negative, bypass, misuse, or failure cases for the behavior a KSI describes where applicable. | Proof records; robustness evidence |
| System/version context | Bind the cloud service offering boundary, configuration, policy, and environment versions in effect during the test. | Environment descriptor |
| Evidence export for review | Package evidence and provenance for independent examination by a provider, agency, assessor, or advisor. | ProofBundle |

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use FedRAMP 20x, another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **FedRAMP 20x supplies Key Security Indicator and certification-rule context. Proof Protocol supplies the evidence model for independently examining whether the behavior a KSI describes actually occurred and produced the claimed outcome.**

No affiliation, endorsement, certification, or sponsorship by GSA or the FedRAMP program is implied. Nebulonium, Inc. is not a FedRAMP recognized assessor, and this specification is not a FedRAMP document.

## 10. Source Framework, Attribution, and License

FedRAMP 20x and the FedRAMP Consolidated Rules for 2026 are published by the FedRAMP program of the U.S. General Services Administration at https://www.fedramp.gov/2026/ (program status at https://www.fedramp.gov/20x/; KSI reference at https://fedramp.gov/2026/reference/key-security-indicators/). A machine-readable rules dataset is published at https://github.com/FedRAMP/rules.

The fedramp.gov pages and FedRAMP GitHub repositories reviewed for this draft do not state a content license. Works prepared by U.S. Government employees as part of their official duties are generally not subject to copyright in the United States (17 U.S.C. 105), but reuse terms for any specific FedRAMP material SHOULD be checked at the authoritative source before reuse.

The FedRAMP name and logo are restricted. The fedramp.gov disclaimers page (https://www.fedramp.gov/disclaimers) states that they are GSA property and "may not be used without GSA's express, written permission." The FedRAMP Branding Guidance (https://www.fedramp.gov/resources/documents/FedRAMP_Branding_Guidance.pdf) further restricts use of the name and logo, including any use implying government endorsement and use in company, product, service, or domain names. This specification uses the FedRAMP name only to identify the external program being referenced. It does not use the FedRAMP logo, does not claim FedRAMP Certification or authorization for any product, and does not imply government endorsement.

This Proof Protocol mapping is independently authored and licensed under **CC BY 4.0**. That license applies only to original Proof Protocol material in this repository. It does not relicense external standards, regulations, criteria, frameworks, or trademarks.

Where upstream material is copyrighted or access-controlled, contributors MUST NOT copy protected normative text into this repository merely to make the mapping self-contained. Reference identifiers and independently authored descriptions should be used where legally appropriate.

### Required attribution

No attribution notice required for referencing FedRAMP content was found on fedramp.gov. The following owner statement is quoted verbatim from https://www.fedramp.gov/disclaimers:

> "The FedRAMP name and the FedRAMP logo are the property of the General Services Administration (GSA)."

Recommended citation: FedRAMP, General Services Administration, *FedRAMP Consolidated Rules for 2026 (CR26)*, Key Security Indicators, https://fedramp.gov/2026/reference/key-security-indicators/ (retrieved October 8, 2026).

What this specification reproduces: KSI theme codes, the KSI identifier format, one example identifier, ruleset names and abbreviations, certification class names, and short factual statements of program status. It does not reproduce KSI statements, rule text, or other FedRAMP descriptive content, and it does not use the FedRAMP logo.

## 11. Versioning

This mapping is versioned independently of FedRAMP 20x. Material upstream changes SHOULD trigger a mapping review and, where necessary, a new version identifying the upstream revision mapped. This version maps CR26 as published at fedramp.gov on October 8, 2026, during Phase Three (Wide-scale Adoption).

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
