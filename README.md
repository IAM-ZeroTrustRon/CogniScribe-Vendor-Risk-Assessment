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

## Training evidence

### Chain Reaction — completion
![Chain Reaction completion: four tasks and 80 points](evidence/Screenshot_chain_reaction_badge.png)

### Governance & Regulation — final exercise
![Governance and Regulation final exercise screenshot](evidence/Screenshot_gov_reg_badge.png)
This captures the exercise flag; full room completion is user-reported.

### Dependency investigation
![Terminal showing typing-coreutils version 1.6.4](evidence/lab-dependency-version.png)
The screenshot records the installed suspicious dependency and also captures an unfinished shell command. It does not demonstrate successful execution of every visible command.

[View the captured postinstall script](evidence/lab-postinstall-script.png) and [read the evidence provenance](evidence/README.md). The script screenshot shows obfuscated source; its decoder key and complete decoded behavior are documented from consolidated notes rather than proved by this screenshot alone.

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
    lab-dependency-version.png
    lab-postinstall-script.png
```

## Assessment boundary
This is a fictional vendor assessment backed by a completed training investigation. See the executive memo for the procurement decision, the register for scoring, and the evidence record for confidence limits. No actual vendor compromise, ePHI exposure or implemented remediation is claimed.

## Primary references
- [NIST CSF supply-chain guide](https://csrc.nist.gov/pubs/sp/1305/final)
- [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework)
- [HHS Security Rule](https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html)
- [HHS Part 2](https://www.hhs.gov/hipaa/part-2/index.html)
- [npm CI](https://docs.npmjs.com/cli/commands/npm-ci/) and [trusted publishing](https://docs.npmjs.com/trusted-publishers/)
