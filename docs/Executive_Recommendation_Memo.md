# Executive Procurement Recommendation

**To:** Chief Information Security Officer and Clinical Procurement Committee  
**From:** Ron Richardson, portfolio assessor  
**Date:** October 4, 2026  
**Subject:** CogniScribe AI — conditional evaluation; production integration withheld

## Executive Summary
Approve a synthetic-data evaluation only. Do not authorize real encounter capture or production EHR integration at this stage. CogniScribe AI is a fictional ambient clinical documentation service; no vendor assurance, contract or control implementation has been received or verified. Its potential documentation benefits must be evaluated alongside the consequences of exposing clinical conversations and writing inaccurate notes into patient records.

This recommendation is informed by completed TryHackMe training and an investigation of a malicious software dependency. The lab demonstrates a credible supply-chain failure mode; it does not prove this fictional vendor is compromised. No budget, measured clinical benefit or quantified financial loss is asserted.

## Scope & Architecture
The proposed workflow captures encounter audio, transcribes it, sends content to an LLM, produces draft SOAP notes and writes clinician-approved content into the EHR. Assess every intermediate copy, external inference API, hosting component, support path, credential and backup. The hospital treats this service as Tier-1/high criticality because it could process direct ePHI and highly sensitive mental-health/SUD content and affect record integrity.

HIPAA applicability, business-associate relationships and HITECH-linked breach duties require legal review. Part 2 applicability depends on the records and parties involved; SUD discussion alone does not make all data a Part 2 record. Ordinary psychiatric documentation must also be distinguished from separately defined psychotherapy notes. NIST AI RMF provides voluntary governance guidance.

## Inherent vs. Residual Risk Analysis
The register contains ten risk scenarios: dependency execution, publisher compromise, persistence, outbound communications, secondary AI use, subprocessors, clinical output errors, EHR privilege, incident response and continuity. Inherent scores range from High to Very High under stated clinical assumptions. All current residual assessments are unknown because controls are unverified.

The proposed treatments reduce likelihood in a conditional model, leaving eight projected High and two projected Moderate risks. These are targets, not achieved reductions. High-consequence clinical exposure remains possible even with controls. Management must review actual effectiveness and explicitly accept remaining High risks individually; a favorable questionnaire or average score cannot authorize release.

## Conditional Approval Terms
Before real data or production connectivity, require:

1. **Legal and data-use gates:** Executed hospital/vendor BAA and appropriate subcontractor assurances; authorized data flows and applicable consent/restriction handling; binding no-training/no-secondary-use terms; downstream inference zero retention; hospital-approved transient retention and deletion/exit terms. Complete legal/privacy review before processing sensitive notes.
2. **Supply-chain gates:** Release SBOM and automated SCA; reviewed locked versions and npm integrity/provenance checks; default lifecycle-script blocking with isolated approved exceptions; ephemeral builds without ePHI or production credentials; constrained egress. Human publisher accounts use FIDO2 MFA; prefer OIDC CI publishing, with scoped, expiring token fallback reviewed as an exception.
3. **Clinical/integration gates:** Approved synthetic validation thresholds, clinician review before finalized writes, verified patient context, minimum EHR scopes, tenant isolation and attributable audit events. Validate rollback and an integration disablement mechanism.
4. **Operational gates:** Tested detection and containment; initial incident notice contractually within 24 hours of discovery of a suspected material incident, with subsequent updates. This is a proposed hospital condition, not a statement of the statutory deadline. Validate proposed four-hour RTO/one-hour RPO, manual clinical fallback and reconciliation after recovery; revise targets only with clinical-owner approval.
5. **Release decision:** Close mandatory evidence gaps, reassess actual residual risk, obtain clinical/legal clearance and CISO/business-owner acceptance of remaining High risks. Very High risk blocks release under the proposed policy. Record scope, conditions, reviewer evidence and decision date.

## Oversight and Decision Record
During evaluation use synthetic encounters only, with no production tokens or patient-data feeds. Review open gates weekly. Following any authorized deployment, reassess annually and after material model, dependency, subprocessor or incident changes. Revoke access and suspend expansion if agreed safeguards fail.

**Decision status: recommendation only; unsigned and not approved.** See the [risk register](Evidence_Gap_Risk_Register.md) for ownership and the [VSQ](Vendor_Security_Questionnaire.md) for requested artifacts.
