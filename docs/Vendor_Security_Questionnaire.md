# CogniScribe AI — Tailored Vendor Security Questionnaire

Deliverable 1 | Ron Richardson | October 4, 2026

## Scope and response protocol
Fictional Tier-1 clinical AI service: audio capture → transcription → LLM inference → draft SOAP notes → clinician review → EHR integration. Include unstructured clinical conversations, ePHI and applicable sensitive records. No vendor responses or controls have been verified. Chain Reaction informs risk questions; its lab findings do not establish vendor weaknesses.

For each question provide implementation status, owner, product/tenant scope, evidence ID/version/date, exceptions and corrective commitment. Justify N/A. Submit redacted artifacts and synthetic test data only. All items are proposed pre-production review gates, subject to hospital reviewer acceptance. Contracts and technical effectiveness must both be reviewed.

### Q01 — Clinical data flow
**Question:** Identify every recipient and copy of encounter audio, transcripts, prompts, outputs, embeddings and telemetry, from capture through clinician-approved EHR write-back.

**Required evidence / review criterion:** Versioned data-flow diagram, field inventory, storage locations and recipient mapping.

### Q02 — No training or secondary use
**Question:** Will vendor and downstream providers prohibit patient-data use for training, fine-tuning, evaluation datasets or product improvement, without opt-in defaults?

**Required evidence / review criterion:** Binding service/downstream terms, tenant settings and synthetic enforcement tests.

### Q03 — Zero data retention
**Question:** Can downstream inference retain no clinical content after processing? Separately explain hospital-authorized transient storage, retry queues, abuse-monitoring exceptions, logs and backups.

**Required evidence / review criterion:** Endpoint-specific retention commitments, configuration, expiry schedule and deletion tests. Zero retention is a procurement requirement, not a universal HIPAA mandate.

### Q04 — Clinical safety
**Question:** How are omissions, hallucinations, medication errors and speaker attribution tested, and how is clinician review required before final EHR entry?

**Required evidence / review criterion:** Synthetic clinical validation, acceptance thresholds, review workflow and denied unapproved-write tests.

### Q05 — AI change governance
**Question:** Who approves model/provider/prompt changes and can stop or roll back unsafe releases? How is encounter text kept from becoming trusted instructions or tool actions?

**Required evidence / review criterion:** Governance roles, change approvals, adversarial/regression tests and rollback demonstration.

### Q06 — BAA contract chain
**Question:** Will the vendor execute a hospital-approved BAA and require appropriate business-associate obligations of applicable ePHI-processing subcontractors?

**Required evidence / review criterion:** BAA and relevant subcontractor provisions. Direct hospital BAAs with every subcontractor are not presumed necessary.

### Q07 — LLM and hosting inventory
**Question:** Which LLM APIs, transcription, hosting, analytics and support services receive data, under which product tiers, regions and responsibilities?

**Required evidence / review criterion:** Current subprocessor inventory, endpoint settings and service-specific assurance. No unapproved or consumer endpoint may receive ePHI.

### Q08 — Subprocessor changes and exit
**Question:** How can the hospital review material downstream changes before transfer and export/delete data on termination?

**Required evidence / review criterion:** Notice/objection terms, synthetic export, exit plan, deletion attestation and backup expiry.

### Q09 — Part 2 and sensitive notes
**Question:** How will you support hospital-determined consent and restrictions for applicable Part 2 records and psychotherapy notes, distinguished from ordinary psychiatric notes?

**Required evidence / review criterion:** Applicability analysis, consent/restriction workflow and role tests. SUD discussion alone does not establish Part 2 applicability.

### Q10 — Release SBOM
**Question:** Do release-specific SBOMs include direct/transitive dependencies, containers and relevant model components, with an emergency inventory search?

**Required evidence / review criterion:** SPDX/CycloneDX sample, release linkage, inventory search and owner.

### Q11 — SCA and malicious packages
**Question:** How do automated checks identify vulnerabilities, malicious packages and risky dependency changes, block releases and track exceptions?

**Required evidence / review criterion:** Pipeline settings, sanitized results, simulated gate failures and triage commitments. Document unknown-malware limitations.

### Q12 — Pinning and integrity
**Question:** Are approved versions locked, installed reproducibly and verified using npm SHA-512 integrity values, with separate artifact provenance checks?

**Required evidence / review criterion:** Reviewed lockfile, npm ci job, integrity-failure test and change approvals. A matching hash does not prove benign code.

### Q13 — Install-script restrictions
**Question:** Do builds enforce npm install --ignore-scripts or npm ci --ignore-scripts, with necessary exceptions individually reviewed and isolated?

**Required evidence / review criterion:** Effective runner configuration, blocked postinstall test and version-specific exception inventory. Separately control explicitly invoked scripts.

### Q14 — Publishing identity
**Question:** Do humans use FIDO2 hardware-backed MFA for registry/source administration, and CI use short-lived OIDC trusted publishing instead of long-lived tokens?

**Required evidence / review criterion:** Enforcement settings, role reviews, OIDC configuration and token scope/expiry inventory. Hardware MFA protects interactive accounts, not bearer-token execution.

### Q15 — Build isolation
**Question:** Can dependency scripts access ePHI, production EHR tokens, cloud secrets or unrestricted egress? Are runners ephemeral and separate from production?

**Required evidence / review criterion:** Runner permissions, secret delivery policy, egress rules and synthetic isolation tests. Require no ePHI or production credentials in builds.

### Q16 — EHR least privilege
**Question:** How are API scopes, patient context, credential rotation and clinician-approved writes enforced?

**Required evidence / review criterion:** Scope inventory, denial tests, token lifecycle and attributable write logs.

### Q17 — Encryption and isolation
**Question:** How are clinical content and credentials protected in transit/storage and isolated between tenants, including caches and backups?

**Required evidence / review criterion:** TLS/storage settings, key permissions, isolation assessment and support-access evidence.

### Q18 — Detection and audit
**Question:** Can you detect unexpected Node child processes, hidden payloads, shell-profile changes and cleartext egress while avoiding clinical content in logs?

**Required evidence / review criterion:** EDR coverage, synthetic detection tests, destination restrictions, redacted event samples, retention and alert ownership.

### Q19 — Incident response
**Question:** What exact contractual initial-notice deadline and updates are offered, and how can you isolate systems, revoke tokens and preserve evidence?

**Required evidence / review criterion:** Hospital-approved terms, escalation roster, tabletop results and subprocessor escalation. Legal review confirms obligations; no universal statutory deadline is assumed.

### Q20 — Continuity and reassessment
**Question:** How will clinical work continue during outage/unsafe output, recovery avoid duplicate writes, and material changes trigger reassessment?

**Required evidence / review criterion:** Approved RTO/RPO, restore/failover and reconciliation tests, clinical fallback and assurance schedule.

## Review record
Track Requested → Received → Reviewed → Accepted or Gap open, with reviewer and date. Unanswered items earn no assurance credit. Evidence receipt does not prove effectiveness. Link unresolved issues to the risk register; projected residual scores remain conditional until verified. Hospital risk, clinical and legal authorities make final approval decisions.

## Sources
- [HHS cloud guidance](https://www.hhs.gov/hipaa/for-professionals/special-topics/health-information-technology/cloud-computing/index.html)
- [HHS business associates](https://www.hhs.gov/hipaa/for-professionals/privacy/guidance/business-associates/index.html)
- [HHS Part 2](https://www.hhs.gov/hipaa/part-2/index.html)
- [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) — voluntary framework, not legislation
- [NIST Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf)
- [npm ci](https://docs.npmjs.com/cli/commands/npm-ci/)
- [npm trusted publishing](https://docs.npmjs.com/trusted-publishers/)
- [npm CI credentials](https://docs.npmjs.com/using-private-packages-in-a-ci-cd-workflow/)
