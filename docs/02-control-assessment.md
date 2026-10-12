# Control assessment (NIST CSF 2.0)

Assessment date: 2026-10-12. The same data is in [controls.csv](../data/controls.csv). Subcategory IDs were checked against the NIST CSF 2.0 text. The outcome wording is a short paraphrase. See the [method](00-methodology.md) for what each status means and the [evidence index](05-evidence-index.md) for the E- references.

**41 subcategories assessed:** 15 Implemented, 23 Partial, 3 Gap.

Subcategories that do not apply to a household environment were left out of scope, not failed.

## Govern

3 Implemented, 2 Partial, 0 Gap

| ID | Outcome | Status | How it is met | Gap | Evidence | Findings |
| --- | --- | --- | --- | --- | --- | --- |
| GV.OC-05 | Outside services the household depends on are understood and communicated | **Implemented** | Suppliers and what happens if each fails are listed in the scope document | None | E-01 | None |
| GV.RM-02 | Risk appetite and tolerance statements are established and maintained | **Implemented** | Appetite and tolerance are written in the methodology and applied to every risk | None | E-01 | None |
| GV.RM-06 | A consistent method for scoring, recording, and ranking risk is used | **Implemented** | A 5 by 5 likelihood and impact method is documented and applied to every register entry | None | E-01 | None |
| GV.PO-01 | A cyber risk policy is established, communicated, and enforced | **Partial** | Four short policies are written and cross-referenced to findings | Policies are new, with no automated checks yet | E-01 | [F-24](04-poam.md) |
| GV.PO-02 | The policy is reviewed and updated | **Partial** | Each policy has an owner and a review date | No review has taken place yet | E-01 | [F-24](04-poam.md) |

## Identify

9 Implemented, 5 Partial, 0 Gap

| ID | Outcome | Status | How it is met | Gap | Evidence | Findings |
| --- | --- | --- | --- | --- | --- | --- |
| ID.AM-01 | Inventories of hardware are maintained | **Implemented** | Hardware listed with role and criticality in the asset inventory | None | E-01 | None |
| ID.AM-02 | Inventories of software, services, and systems are maintained | **Implemented** | Every service is in the inventory, defined in a compose file, and pinned to a version | None | E-01, E-03 | None |
| ID.AM-03 | Authorized network communications and data flows are mapped | **Partial** | Architecture, DNS, remote access, and backup flows are diagrammed | Not every flow is mapped | E-01 | [F-24](04-poam.md) |
| ID.AM-04 | Inventories of services provided by suppliers are maintained | **Implemented** | Suppliers are listed with what each provides | None | E-01 | None |
| ID.AM-05 | Assets are prioritized by classification and criticality | **Implemented** | Each asset has a criticality rating and each data set a classification | None | E-01 | None |
| ID.AM-07 | Inventories of data and metadata are maintained | **Partial** | Data types, classification, and location are listed | No owner or retention period recorded per data set | E-01 | [F-24](04-poam.md) |
| ID.AM-08 | Assets are managed throughout their life cycles | **Partial** | Retired services were removed completely, including their jobs, rules, and credentials | No end-of-life tracking for hardware or software | E-06, E-08, E-09 | [F-18](04-poam.md), [F-24](04-poam.md) |
| ID.RA-01 | Vulnerabilities in assets are identified, validated, and recorded | **Partial** | This assessment found and recorded configuration weaknesses, each verified on the server | No vulnerability scanning or advisory monitoring | E-12 | [F-18](04-poam.md) |
| ID.RA-05 | Threats, vulnerabilities, likelihoods, and impacts are used to rank risk | **Implemented** | Every risk has a likelihood, impact, and score using the documented method | None | E-12 | None |
| ID.RA-06 | Risk responses are chosen, prioritized, planned, and tracked | **Implemented** | Each risk has a treatment. Each finding has an action, an owner, a date, and a status | None | E-12 | None |
| ID.RA-07 | Changes and exceptions are managed, assessed, recorded, and tracked | **Implemented** | Change management policy requires a record. Decisions are written as decision records. Accepted risks carry a review date | None | E-11 | None |
| ID.IM-01 | Improvements are identified from evaluations | **Implemented** | A configuration audit found that published documentation overstated some controls. The documentation was corrected and each weakness became a tracked finding | None | E-12 | [F-08](04-poam.md) |
| ID.IM-03 | Improvements are identified from operational activities | **Implemented** | Blameless incident reviews led to concrete changes, such as a reserved ports table after an outage | None | E-10 | None |
| ID.IM-04 | Incident response and other plans are created, kept current, and improved | **Partial** | Incident response and backup policies are written | The plans have not been exercised | E-10 | [F-10](04-poam.md) |

## Protect

2 Implemented, 12 Partial, 1 Gap

| ID | Outcome | Status | How it is met | Gap | Evidence | Findings |
| --- | --- | --- | --- | --- | --- | --- |
| PR.AA-01 | Identities and credentials are managed | **Partial** | Self-hosted password manager. Household members have separate logins. Router administrator password changed. Credentials left by retired services were removed | No periodic access review yet | E-08, E-13, E-15, E-18, E-22 | [F-11](04-poam.md), [F-24](04-poam.md) |
| PR.AA-03 | Users, services, and hardware are authenticated | **Partial** | SSH accepts keys only. The private network uses device identity. Two-factor is on Home Assistant | Two-factor is not on every service. Passphrase protection of the laptop key is not yet confirmed | E-02, E-14 | [F-11](04-poam.md), [F-27](04-poam.md) |
| PR.AA-05 | Access rights follow least privilege and are reviewed | **Partial** | The dashboard uses view-only accounts. The Docker socket was removed from one monitoring container and put behind a read-only filtering proxy for the other | Private network access rules are permissive. The LAN is flat | E-04, E-12 | [F-12](04-poam.md), [F-25](04-poam.md) |
| PR.DS-01 | Data at rest is protected | **Partial** | The password vault is encrypted by the application. Its backups are encrypted with a key kept offline | Server and media drive are not encrypted | E-05, E-16, E-20 | [F-17](04-poam.md) |
| PR.DS-02 | Data in transit is protected | **Partial** | Remote access uses the encrypted private network. Sensitive apps are served over HTTPS on it | Services reached by local name on the LAN use plain HTTP | E-01, E-08 | [F-22](04-poam.md) |
| PR.DS-11 | Backups are created, protected, maintained, and tested | **Partial** | Nightly encrypted password vault backup on two disks. Home Assistant backs up to cloud storage. A decryption test passed | Photos, files, and media have no second copy. Vault backups share one machine. No full restore drill | E-05, E-16 | [F-09](04-poam.md), [F-10](04-poam.md) |
| PR.PS-01 | Configuration management practices are established and applied | **Implemented** | Every service is defined in a compose file with pinned versions. Changes are made one at a time and documented | None | E-01, E-03 | None |
| PR.PS-02 | Software is maintained, replaced, and removed commensurate with risk | **Partial** | Versions are pinned and updated deliberately | No regular update review and no advisory watching | E-03 | [F-18](04-poam.md) |
| PR.PS-03 | Hardware is maintained, replaced, and removed commensurate with risk | **Partial** | The server is repurposed hardware that is monitored | No hardware replacement plan | E-01 | [F-24](04-poam.md) |
| PR.PS-04 | Log records are generated and available for monitoring | **Partial** | Services and DNS keep their own logs | No central collection, retention rule, or regular review | E-01 | [F-23](04-poam.md) |
| PR.PS-05 | Installation and execution of unauthorized software are prevented | **Partial** | Images come from known publishers and are pinned. Administrative access needs a key | No image signature checks | E-03 | [F-18](04-poam.md) |
| PR.IR-01 | Networks and environments are protected from unauthorized logical access | **Partial** | No router port forwards. DNS filtering. A host firewall. Remote access only through the private network | Container-published ports are not governed by the host firewall. Redundant firewall rules remain. The LAN is flat | E-06, E-23 | [F-12](04-poam.md), [F-15](04-poam.md), [F-16](04-poam.md) |
| PR.IR-02 | Assets are protected from environmental threats | **Gap** | None | No battery backup for the server or network equipment | E-20 | [F-13](04-poam.md) |
| PR.IR-03 | Mechanisms achieve resilience requirements in normal and adverse situations | **Partial** | Home Assistant is backed up to the cloud. Monitoring detects outages | One DNS server. No second copy of core data | E-01 | [F-09](04-poam.md), [F-14](04-poam.md) |
| PR.IR-04 | Adequate resource capacity is maintained | **Implemented** | Host metrics are monitored. The system volume was extended on 2026-10-12 and is about half full, with more unallocated space available | None | E-17, E-24 | [F-19](04-poam.md) |

## Detect

0 Implemented, 2 Partial, 1 Gap

| ID | Outcome | Status | How it is met | Gap | Evidence | Findings |
| --- | --- | --- | --- | --- | --- | --- |
| DE.CM-01 | Networks and network services are monitored for adverse events | **Partial** | DNS query logs and service availability checks | No intrusion detection | E-01 | [F-23](04-poam.md) |
| DE.CM-03 | Personnel activity and technology usage are monitored | **Gap** | None | Login attempts are not reviewed or alerted on | E-01 | [F-23](04-poam.md) |
| DE.CM-09 | Computing hardware and software are monitored for adverse events | **Partial** | Host metrics and container health monitors | No alerts for security events | E-01 | [F-23](04-poam.md) |

## Respond

1 Implemented, 1 Partial, 0 Gap

| ID | Outcome | Status | How it is met | Gap | Evidence | Findings |
| --- | --- | --- | --- | --- | --- | --- |
| RS.MA-01 | The incident response plan is executed once an incident is declared | **Partial** | An incident response policy exists. Real outages were handled and reviewed | The plan has not been exercised | E-10 | [F-10](04-poam.md) |
| RS.AN-03 | Analysis establishes what happened and the root cause | **Implemented** | Each incident write-up records the timeline, root cause, and the change made | None | E-10 | None |

## Recover

0 Implemented, 1 Partial, 1 Gap

| ID | Outcome | Status | How it is met | Gap | Evidence | Findings |
| --- | --- | --- | --- | --- | --- | --- |
| RC.RP-03 | The integrity of backups is verified before restoration | **Partial** | The backup job checks the archive before encrypting it. A decryption test passed | No written restore procedure that includes an integrity check | E-05, E-16 | [F-10](04-poam.md) |
| RC.RP-05 | The integrity of restored assets is verified and services are restored | **Gap** | Not yet demonstrated | No full restore into a working service has been run | E-05 | [F-10](04-poam.md) |
