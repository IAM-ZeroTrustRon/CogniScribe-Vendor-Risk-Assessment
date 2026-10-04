# Third-Party Vendor Risk Assessment & Software Supply Chain Governance

![Type](https://img.shields.io/badge/assessment-fictional_vendor-blue) ![Lab](https://img.shields.io/badge/Chain_Reaction-4_tasks%20%7C%2080_points-green) ![Status](https://img.shields.io/badge/production_approval-withheld-orange)

**Ron Richardson | Healthcare GRC & IAM Portfolio — Project 2 | October 4, 2026**

CogniScribe AI is a fictional ambient clinical documentation platform processing encounter audio into draft SOAP notes for EHR integration. This case study turns supply-chain investigation lessons into procurement evidence requests, risk decisions and enforceable release gates. No real vendor assessment, patient data or production testing is represented.

## Read by purpose
| Deliverable | Reader and purpose |
|---|---|
| [Vendor security questionnaire](docs/Vendor_Security_Questionnaire.md) | Vendor/reviewers: twenty questions and required artifacts |
| [Evidence-gap risk register](docs/Evidence_Gap_Risk_Register.md) | Risk owners: ten scenarios, assumptions, gaps, treatment and conditional residual scores |
| [Executive procurement memo](docs/Executive_Recommendation_Memo.md) | CISO/committee: synthetic evaluation recommendation and production gates |
| [Technical evidence](evidence/README.md) | Reviewers: completion screenshots, lab findings and confidence boundaries |

## Training to governance
Chain Reaction completion is evidenced by four tasks and 80 points. Governance & Regulation completion is user-reported with a final-exercise screenshot. The lab dependency differs from the public incident reference: the captured scenario uses typing-coreutils, so public-report package names are not substituted for lab observations.

| Lab observation | Vendor governance consequence | VSQ |
|---|---|---|
| Injected transitive package and install hook | Review dependency changes and block unapproved lifecycle execution | Q10–Q13 |
| Obfuscated downloader and HTTP C2 | Isolate builds, constrain egress and test runtime detection | Q15,Q18 |
| Reported disguised payload/profile persistence | Test startup-change detection and containment; retain raw substantiation | Q18,Q19 |
| Exposure possible through a trusted component | Establish recipient/data boundaries and minimum EHR permissions; do not assume exfiltration | Q01,Q07,Q16 |

## Framework mapping matrix
Mappings are review objectives, not findings of legal violation or NIST certification. AI RMF is voluntary; HIPAA applicability and Part 2 handling require legal analysis.

| Review area | NIST CSF 2.0 category | HIPAA review area | AI RMF function | VSQ |
|---|---|---|---|---|
| Vendor/dependency governance | GV.SC — supply chain | Risk analysis/management §164.308(a)(1); BA safeguards §164.308(b) | GOVERN | Q06–Q15 |
| Data purpose and recipients | ID.AM — asset management; GV.OC — context | Permitted use/disclosure and BAA scope §§164.502,164.504(e) | MAP/GOVERN | Q01–Q03,Q06–Q09 |
| Identity and clinical integration | PR.AA — identity/access | Access, authentication, integrity §164.312(a),(c),(d) | GOVERN/MEASURE | Q14,Q16,Q17 |
| Build, runtime and transmission | PR.PS — platform security; PR.DS — data security | Risk management; transmission §164.312(e) | MEASURE/MANAGE | Q10–Q18 |
| Incident handling | DE.CM — monitoring; RS.MA — incident management | Incident procedures §164.308(a)(6); BA notification §164.410 | MANAGE | Q18,Q19 |
| Clinical validation and continuity | ID.RA — risk assessment; RC.RP — recovery execution | Integrity §164.312(c); contingency §164.308(a)(7); broader clinical safety assessed separately | MEASURE/MANAGE | Q04,Q05,Q20 |

## File structure
```
CogniScribe-AI/
  README.md
  docs/
    Vendor_Security_Questionnaire.md
    Evidence_Gap_Risk_Register.md
    Executive_Recommendation_Memo.md
  evidence/
    README.md
    Screenshot_gov_reg_badge.png
    Screenshot_chain_reaction_badge.png
```

## Decision and limitations
Production approval is withheld. All vendor gaps are open; current residual risk is unknown. Projected treatment leaves eight High and two Moderate risks, requiring fresh evidence-based assessment and explicit owner decisions. Clinical/legal gates cannot be replaced by technical risk acceptance.

Some forensic details came from consolidated notes rather than raw artifacts visible in this chat; see the evidence record. No actual ePHI exposure, patient harm, credential theft or vendor remediation is claimed. This documentation package has been assembled locally; GitHub publication is not yet verified.

## Primary references
- [NIST CSF supply-chain guide](https://csrc.nist.gov/pubs/sp/1305/final)
- [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework)
- [HHS Security Rule](https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html)
- [HHS Part 2](https://www.hhs.gov/hipaa/part-2/index.html)
- [npm CI](https://docs.npmjs.com/cli/commands/npm-ci/) and [trusted publishing](https://docs.npmjs.com/trusted-publishers/)
