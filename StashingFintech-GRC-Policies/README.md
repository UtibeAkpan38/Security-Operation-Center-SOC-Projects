# StashingFintech GRC Policies

Ten information security policies for StashingFintech, a fictional Nigerian payments company. This repository holds the report that explains how our team built, reviewed, approved and rolled out the policies. I worked on the project as the company's IAM Specialist.

> **About the company:** StashingFintech is a fictional company our team of eight created for a governance, risk and compliance (GRC) project. Every policy names roles and never people. No real company data appears in this repository.

## Why compliance matters

Everyone who touches customer data needs to know the rules. A rule that nobody can explain protects nobody. My background is SOC analysis, so compliance sits outside my usual field. This project showed me that detection work and policy work depend on each other. A SOC analyst who knows the policy behind an alert can judge it faster and report it better.

## The company

| Item | StashingFintech |
|---|---|
| What it does | Payments for merchants and individuals across Nigeria |
| Products | Online checkout, POS terminals, bank transfers, virtual accounts, payment cards and a mobile app |
| Size | About 250 employees plus customer support contractors |
| Location | Head office in Lagos, with staff in the office and at home |
| Data it holds | Names, phone numbers, BVN, ID documents, bank details, card data, transaction records and staff records |
| Biggest risks | Phishing and social engineering, account takeover, insider misuse, supplier breaches, data leaks and service outages |
| Rules it must meet | CBN rules for payment service providers, NDPA 2023, GAID 2025, Cybercrimes (Amendment) Act 2024, PCI DSS v4.0.1 and ISO/IEC 27002:2022 |

## My role

As IAM Specialist, I:

1. Wrote **SF-POL-004 Privileged Account Policy**.
2. Reviewed **SF-POL-003 Identity Management and Access Control Policy** and **SF-POL-007 Clear Desk and Clear Screen Policy**.
3. Revised my policy after review, from version 0.1 to version 0.2.
4. Prepared and presented to the Board of Directors how I developed the policy.

## The policy set

All ten policies reached version 1.0 and received approval on 15 November 2026. Roles come from each policy's document control page.

| ID | Policy | Written by | Reviewed by | Approved by |
|---|---|---|---|---|
| SF-POL-001 | Information Security Policy | Information Security Manager | Head of Risk and Compliance | Board of Directors (signed by CEO) |
| SF-POL-002 | Information Classification Policy | Head of Data and AI | DPO | CEO |
| SF-POL-003 | Identity Management and Access Control Policy | CTO | IAM Specialist | CISO |
| **SF-POL-004** | **Privileged Account Policy** | **IAM Specialist** | **CTO** | **CISO** |
| SF-POL-005 | AI Policy | CTO | DPO | CEO |
| SF-POL-006 | Incident Management Policy | Information Security Manager | Head of Risk and Compliance | CEO |
| SF-POL-007 | Clear Desk and Clear Screen Policy | CISO | IAM Specialist | CEO |
| SF-POL-008 | Data Protection and Privacy Policy | DPO | Head of Data and AI | CEO |
| SF-POL-009 | Supplier and Third-Party Security Policy | Head of Risk and Compliance | CISO | CEO |
| SF-POL-010 | Cryptography and Key Management Policy | Security Engineer | Information Security Manager | CISO |

## My policy: SF-POL-004 Privileged Account Policy

A privileged account is any account that can change system settings, change other people's access, view or change customer data in bulk, move money or manage encryption keys. A stolen or misused account of this kind can hurt customers and the business far more than an ordinary account. StashingFintech names phishing, account takeover and insider misuse among its biggest risks, so this policy controls who holds these accounts, how they use them and how we check them.

**ISO/IEC 27002:2022 placement:** theme 8 Technological, control 8.2 Privileged access rights. Supporting controls: 5.3, 5.15, 5.16, 5.17, 5.18, 8.5 and 8.15.

**Selected rules:**

| Area | What the policy requires |
|---|---|
| Register | The IAM Specialist keeps one register of every privileged account |
| Approval | The CISO decides each request in writing within 2 working days. The person who approves never grants the access |
| Authentication | Every privileged login uses a phishing-resistant method, and privileged sessions lock after 15 minutes of inactivity |
| Emergency access | Emergency (break glass) accounts need approval, a review within 1 working day and a credential reset within 24 hours |
| Logging | Every privileged action is logged, kept for at least 12 months and reviewed every week |
| High-risk actions | The admin dashboard needs a second approver to move money or export customer data in bulk |
| Contractors and suppliers | Privileged accounts end within 90 days, and the outsourced support team never receives super-admin rights |
| Reviews | The IAM Specialist reviews all privileged accounts every quarter |
| Leavers | Privileged access ends within 24 hours of a leaver's last day |
| Misuse | Anyone who suspects misuse reports it within 1 hour |

The approved text is in Appendix C of the full report.

### What review changed

My policy received 11 review comments. I changed these points in version 0.2:

- Contractor and supplier privileged accounts now expire within 90 days, which matches SF-POL-003.
- A mover's access now ends on the day the change takes effect.
- Privileged logins now require a phishing-resistant method.
- The CISO must decide access requests within a set time, and a deputy can approve emergency access.
- Every timed rule now has a matching row in the Policy Compliance Framework.

### What I reviewed

I checked SF-POL-003 and SF-POL-007 against our writing guide, the company profile and ISO/IEC 27002:2022. I tied every comment to one of those sources. The main findings were rules with no named role, timed rules with no compliance check and gaps against the company profile, such as office access, AI tools and partner portals.

## How the project ran

1. **One guide and template.** A team writing guide set the company profile, a fixed list of role titles and a common layout for all ten policies.
2. **Mapped to ISO/IEC 27002:2022.** Each author identified the controls behind their policy and covered them in our own words.
3. **Review in role.** A second person, playing a StashingFintech role, reviewed each draft and returned written comments.
4. **Approval.** The Board, CEO and CISO approved version 1.0 of each policy on 15 November 2026.
5. **Communication.** We published every policy in Wizer, a security awareness platform, and staff read and acknowledged each one.
6. **Compliance framework.** Every timed rule became a scheduled check in the Policy Compliance Framework.

## Results

| Result | Figure |
|---|---|
| Policies approved at version 1.0 | 10 |
| ISO/IEC 27002:2022 controls addressed | 47 of 93 |
| Assigned staff who acknowledged every policy in Wizer | 8 of 8 |
| Compliance checks scheduled for 2027 | 103 |

## What I learned

- **Compliance skills.** I learned the parts of a policy and why each one exists. I learned to give every rule a role, an action and a deadline. I also learned to map a policy to a standard and to check that different policies agree with each other.
- **Review skills.** I learned to base every review comment on a source and to take review comments on my own work without defensiveness.
- **Communication skills.** Preparing and presenting the work forced me to explain every rule in plain words and to say where each number came from. That work helped me understand all ten policies and not only my own.

## Read the full report

The complete report is here: **[StashingFintech GRC Policy Report (PDF)](documents/StashingFintech_GRC_Policy_Report.pdf)**

It covers the company and its obligations, how we developed the policies, alignment with ISO/IEC 27002:2022, key rules from every policy, approval and rollout evidence, the Policy Compliance Framework and recommendations. Appendix C holds all ten approved policies.

## Repository structure

```text
StashingFintech-GRC-Policies/
├── README.md
└── documents/
    └── StashingFintech_GRC_Policy_Report.pdf
```

## Standards and laws referenced

- ISO/IEC 27002:2022
- PCI DSS v4.0.1
- Nigeria Data Protection Act (NDPA) 2023
- GAID 2025
- CBN rules for payment service providers
- Cybercrimes (Amendment) Act 2024

## Author

**Utibe Anthony Akpan**, IAM Specialist, StashingFintech GRC project


This repository documents a training project. It does not give legal advice.
