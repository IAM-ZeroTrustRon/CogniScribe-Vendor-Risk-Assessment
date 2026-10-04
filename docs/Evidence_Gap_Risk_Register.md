# Evidence-Gap Risk Register

October 4, 2026 | Fictional procurement assessment | All gaps OPEN

## Scoring and interpretation
Likelihood: 1 rare, 2 unlikely, 3 plausible, 4 likely, 5 highly likely. Impact: 1 negligible, 2 limited rework, 3 material operational disruption, 4 major disruption/disclosure, 5 severe clinical harm or sensitive-data exposure. Product bands: 1–4 Low, 5–9 Moderate, 10–16 High, 17–25 Very High. Scores are transparent analyst assumptions, not observed probabilities or monetary losses.

Inherent scores assume clinical data and EHR integration without assurance credit. Likelihood 4 marks direct dependency/identity exposure or central AI processing; 3 marks contingent paths. Impact 5 reflects sensitive clinical content or record integrity; response/continuity risks receive 4 given a proposed manual fallback. Projected likelihood 2 is a conditional target only: controls are assumed effective for the projection but have not been tested. Impact is held constant. Current residual risk is UNKNOWN for every row; no control or risk reduction has been verified.

**Potential obligation / framework alignment** identifies relevant review areas: missing evidence does not establish a legal violation, and NIST AI RMF is voluntary. Specific technology controls below are hospital procurement conditions, not claims that HIPAA mandates npm commands or SBOM formats.

| Risk ID | Vulnerability / Threat Scenario | Inherent Risk Level | Control Deficiency | Potential obligation / framework alignment | Mandatory Compensating Control / Treatment | Projected Residual Risk |
|---|---|---|---|---|---|---|
| R01 | Compromised transitive dependency executes during installation; a clinical service build could expose credentials or alter deployed software | 4 x 5 = 20 — Very High | G01: no release-specific SBOM, dependency-review or install-hook evidence | §164.308(a)(1)(ii)(A)–(B); AI RMF GOVERN/MANAGE | SBOM + SCA; approved lockfile/integrity/provenance; default --ignore-scripts and isolated exceptions; restricted build secrets/egress | 2 x 5 = 10 — High |
| R02 | Stolen publisher credential enables a trusted-looking malicious release | 4 x 5 = 20 — Very High | G02: publishing access and credential lifecycle unsubstantiated | §164.312(a),(d); AI RMF GOVERN | FIDO2 for interactive users; OIDC publishing; tightly scoped expiring fallback tokens; reviewed releases | 2 x 5 = 10 — High |
| R03 | Payload masquerades as a utility and modifies shell startup; clinical workloads could remain compromised | 3 x 5 = 15 — High | G03: endpoint detection, runtime isolation and startup-change visibility unverified | §164.308(a)(5),(6); §164.312(b); AI RMF MEASURE/MANAGE | Test interpreter/masquerading/profile-change detection; ephemeral runners; host isolation and rebuild playbook | 2 x 5 = 10 — High |
| R04 | Unauthorized outbound communication could carry clinical content or integration credentials | 4 x 5 = 20 — Very High | G04: destination controls and monitoring not evidenced; lab HTTP C2 does not establish vendor exfiltration | §164.312(e); AI RMF MAP/MANAGE | Approved encrypted destinations; default-deny egress; monitor attempted exceptions; narrowly scoped credentials | 2 x 5 = 10 — High |
| R05 | LLM provider retains encounters or reuses them for training beyond the approved purpose | 4 x 5 = 20 — Very High | G05: no endpoint retention proof or binding no-training terms | §164.502(a),(e); §164.504(e); AI RMF GOVERN/MAP | No secondary-use contracts; inference zero-retention configuration; bounded transient vendor storage and verified deletion | 2 x 5 = 10 — High |
| R06 | Unapproved subprocessor receives ePHI without an appropriate contract chain or restrictions | 3 x 5 = 15 — High | G06: data flow, BAAs and Part 2 handling review absent | §164.308(b); §164.504(e); applicable 42 CFR Part 2; AI RMF GOVERN/MAP | Vendor BAA; applicable subcontractor assurances; reviewed destinations and consent/restriction workflows; change approval | 2 x 5 = 10 — High |
| R07 | Fabricated or misattributed SOAP content reaches the EHR and influences care | 4 x 5 = 20 — Very High | G07: no clinical validation or enforced human-review evidence | §164.312(c) for ePHI integrity; AI RMF MEASURE/MANAGE; clinical safety goes beyond HIPAA | Synthetic clinical/adversarial validation; patient-context checks; clinician approval; rollback and model change gates | 2 x 5 = 10 — High |
| R08 | Overprivileged integration permits cross-patient access or unauthorized EHR changes | 3 x 5 = 15 — High | G08: API scopes, tenant isolation and audit controls unverified | §164.312(a)–(d); AI RMF GOVERN/MEASURE | Minimum integration scopes; patient and tenant isolation tests; token rotation; attributable writes | 2 x 5 = 10 — High |
| R09 | Delayed notification prevents timely hospital containment and legally required response | 3 x 4 = 12 — High | G09: no agreed notification terms or response exercise | §164.308(a)(6); §164.410; AI RMF MANAGE | Contractual initial notice within 24 hours of discovery of a suspected material incident; ongoing updates; tested escalation and forensics | 2 x 4 = 8 — Moderate |
| R10 | Service failure, incomplete recovery or lock-in disrupts documentation and record availability | 3 x 4 = 12 — High | G10: no tested recovery, fallback or usable exit evidence | §164.308(a)(7); AI RMF MANAGE | Proposed 4-hour RTO/1-hour RPO validated by restore test; clinical manual fallback; synthetic export and deletion agreement | 2 x 4 = 8 — Moderate |

## Gap ownership and evidence gates

D0 means hospital authorization of due diligence; targets are proposals. G01–G08: D0+10 business days; G09–G10: D0+15 business days. No production access is allowed while a required gap remains open.

| Gap / risk | VSQ items | Buyer reviewer | Closure requirement |
|---|---|---|---|
| G01 / R01 | Q10–Q13,Q15 | Security engineering | Release-linked SBOM reconciled to lockfile; synthetic unapproved postinstall blocked; build isolation and integrity gates tested |
| G02 / R02 | Q14 | IAM lead | Human publisher MFA and minimal roles verified; CI OIDC binding tested; fallback token scopes, expiry and revocation accepted |
| G03 / R03 | Q15,Q18,Q19 | Security operations | Synthetic profile modification and disguised interpreter execution detected; isolation/rebuild drill evidence accepted |
| G04 / R04 | Q15–Q18 | Cloud security | Unauthorized cleartext destination denied in synthetic test; approved encrypted routes and alert response verified |
| G05 / R05 | Q01–Q03 | Privacy lead | No-training commitments accepted across recipients; endpoint retention settings and queue/deletion tests verified |
| G06 / R06 | Q06–Q09 | Privacy/legal | Data recipients reconciled to contract chain; legal review of applicable restrictions complete; downstream-change controls accepted |
| G07 / R07 | Q04,Q05,Q16 | Clinical safety lead | Clinical validation thresholds met on synthetic cases; clinician review and rollback gates demonstrated |
| G08 / R08 | Q16–Q18 | EHR integration lead | Cross-patient/cross-tenant negative tests pass; API scopes reviewed; token lifecycle and attributable writes demonstrated |
| G09 / R09 | Q19 | Incident response/legal | Notification terms executed; tabletop shows required contacts, evidence preservation and subprocessor escalation |
| G10 / R10 | Q08,Q20 | Clinical operations/continuity | Restore meets approved RTO/RPO; clinical fallback and reconciliation exercised; export and deletion obligations accepted |

## Acceptance rule
Even projected residual risks remain High for R01–R08. Do not call the vendor low risk or approve by averaging scores. Production requires evidence review, a fresh residual assessment and explicit CISO/business-owner acceptance of each remaining High risk. Very High risk blocks release under this proposed policy. Legal prerequisites and clinical-safety gates remain mandatory; they cannot be overridden through ordinary risk acceptance. Otherwise restrict evaluation to synthetic data.

Sources: [HHS Security Rule](https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html), [HHS risk analysis](https://www.hhs.gov/hipaa/for-professionals/security/guidance/final-guidance-risk-analysis/index.html), [HHS BA guidance](https://www.hhs.gov/hipaa/for-professionals/privacy/guidance/business-associates/index.html), [HHS Part 2](https://www.hhs.gov/hipaa/part-2/index.html), [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework). These mappings identify review areas, not certification or legal findings.
