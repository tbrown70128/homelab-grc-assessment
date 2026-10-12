# Home lab GRC assessment

A governance, risk, and compliance (GRC) assessment of my own home lab, built from evidence I collected on the live server. It shows the full cycle a GRC analyst works through: define scope, inventory assets, assess controls against NIST CSF 2.0, score risk, write policy, and track fixes until they are verified.

The lab itself is documented in [homelab-docs](https://github.com/tbrown70128/homelab-docs). This repo is the assessment of that lab.

**Assessment date:** 2026-10-12. **Assessor:** the administrator (self-assessment, no independence). This is not an audit, a certification, or a claim of compliance with any framework.

## Results at a glance

| | |
| --- | --- |
| Subcategories assessed | 41: 14 Implemented, 24 Partial, 3 Gap |
| Risks in the register | 17: 4 High, 12 Moderate, 1 Low today. After planned treatment: 0 High, 6 Moderate, 11 Low |
| Findings | 27: 10 closed and verified, 15 open, 1 blocked, 1 accepted |

### What I fixed and verified

The assessment found real weaknesses, and I fixed and checked the most serious ones before writing this up:

- SSH accepted passwords. It is now key-only, and I confirmed a password attempt is refused.
- Two monitoring containers held control of Docker. One no longer has it. The other reaches Docker only through a read-only filtering proxy.
- Password vault backups were unencrypted. They are now encrypted with a key kept offline, and I tested decryption.
- Four containers could change version on their own. Every container is now pinned to a version.
- Leftovers from retired services, including credentials, certificates, scheduled jobs, and firewall rules, were removed.
- My published documentation overstated several controls. I compared each claim with the live configuration and corrected it.

### What is still open

The five highest current risks:

| Risk | Score | Treatment | Due or review |
| --- | --- | --- | --- |
| [R-01](docs/03-risk-register.md) Loss of irreplaceable data | 15 (High) | Mitigate | 2026-12-31 |
| [R-04](docs/03-risk-register.md) Account compromise where two-factor is off | 12 (High) | Mitigate | 2026-11-01 |
| [R-05](docs/03-risk-register.md) Compromised smart home device reaches servers | 12 (High) | Mitigate | 2027-03-31 |
| [R-06](docs/03-risk-register.md) Power loss or surge damages data or hardware | 12 (High) | Mitigate | 2026-12-31 |
| [R-09](docs/03-risk-register.md) Container ports reachable from the LAN | 9 (Moderate) | Mitigate | 2026-12-15 |

The largest is that photos and documents exist in one place only. Leaving open items visible is deliberate. A register with nothing in it is not credible.

## Read it in this order

| Document | What it is |
| --- | --- |
| [Method](docs/00-methodology.md) | Standard used, status definitions, risk scoring, risk appetite, limits |
| [Scope and assets](docs/01-scope-and-assets.md) | What is covered, the asset and data inventory, suppliers, backup data flow |
| [Control assessment](docs/02-control-assessment.md) | NIST CSF 2.0 subcategories with status, evidence, and gaps |
| [Risk register](docs/03-risk-register.md) | Risks scored by likelihood and impact, with treatment and target dates |
| [Plan of action](docs/04-poam.md) | Findings with action, owner, target date, status, and evidence |
| [Evidence index](docs/05-evidence-index.md) | What was captured, when, and what it showed |

Policies, each one page:

- [Access control](policies/access-control.md)
- [Backup and recovery](policies/backup-and-recovery.md)
- [Change management](policies/change-management.md)
- [Incident response](policies/incident-response.md)

Machine-readable versions of the tables are in [data/](data/): `controls.csv`, `risks.csv`, and `poam.csv`.

## About the evidence

Raw captures contain private addresses and names, so they are not published. The evidence index records what each capture showed. Details that would help an attacker are left out on purpose. Statements I could not capture, such as whether two-factor is on, are marked as owner attestations.

## Planned next

- A small Python check that validates the CSV files and the links between controls, risks, findings, and evidence, run by a GitHub Action on every change
- A first policy review and the first six-month reassessment, due 2027-04-12

## About me

I am moving into GRC after 12 years leading aviation operations under FAA and TSA requirements. Profile: [tbrown70128](https://github.com/tbrown70128). LinkedIn: [terencebrown70128](https://www.linkedin.com/in/terencebrown70128).
