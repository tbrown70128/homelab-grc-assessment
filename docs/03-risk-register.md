# Risk register

Assessment date: 2026-10-12. The same data is in [risks.csv](../data/risks.csv). Scores use the likelihood and impact scales in the [method](00-methodology.md). The current score counts the controls in place today. The target score is what the planned treatment should achieve.

**Risk appetite:** low appetite for loss of irreplaceable data and for compromise of the password vault. Moderate appetite for temporary loss of convenience services. Every High or Critical risk needs a treatment plan with a target date.

## Summary

| Rating | Risks now | Risks after planned treatment |
| --- | --- | --- |
| Critical | 0 | 0 |
| High | 4 | 1 |
| Moderate | 10 | 5 |
| Low | 1 | 9 |

## Register, highest score first

| ID | Risk | L | I | Score | Rating | Treatment | Planned action | Target | Findings | Due or review |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| R-01 | **Loss of irreplaceable data**. A drive failure, theft, fire, or mistake destroys the only copy of family photos and documents | 3 | 5 | 15 | High | Mitigate | Stage 1: a second copy on a separate machine once the spare Raspberry Pi has its drive. Stage 2: an encrypted offsite copy, deferred by the owner and revisited by 2027-04-30. The risk stays High until stage 2 is done | 10 (High) | [F-09](04-poam.md) | 2026-12-31 |
| R-04 | **Account compromise where two-factor is off**. A stolen or guessed password gives access to a service that holds private data | 3 | 4 | 12 | High | Mitigate | Turn on two-factor on every service that supports it and confirm the laptop SSH key has a passphrase | 4 (Low) | [F-11](04-poam.md), [F-27](04-poam.md) | 2026-11-01 |
| R-05 | **Compromised smart home device reaches servers**. A vulnerable device on the flat network scans or attacks the lab server | 3 | 4 | 12 | High | Mitigate | Plan and test network segmentation one device group at a time | 6 (Moderate) | [F-12](04-poam.md) | 2027-03-31 |
| R-06 | **Power loss or surge damages data or hardware**. An outage or surge corrupts the database or disk, or damages the server | 4 | 3 | 12 | High | Mitigate | Buy and install a battery backup for the server and network equipment | 6 (Moderate) | [F-13](04-poam.md) | 2026-12-31 |
| R-09 | **Container ports reachable from the LAN**. A service published by a container is reachable from any device on the LAN, because the host firewall does not govern it | 3 | 3 | 9 | Moderate | Mitigate | Bind sensitive services to localhost or the private network, add DOCKER-USER rules, and remove redundant rules | 3 (Low) | [F-15](04-poam.md), [F-16](04-poam.md) | 2026-12-15 |
| R-11 | **Outdated software with known flaws**. A pinned image falls behind and a known flaw is exploited from the LAN or the private network | 3 | 3 | 9 | Moderate | Mitigate | Set a monthly update review and watch advisories for the services in use | 6 (Moderate) | [F-18](04-poam.md) | 2026-11-15 |
| R-17 | **Security events go unnoticed**. Repeated login failures or odd behavior are not seen because logs are not reviewed or alerted on | 3 | 3 | 9 | Moderate | Mitigate | Collect key logs in one place and alert on login failures | 6 (Moderate) | [F-23](04-poam.md) | 2027-02-28 |
| R-02 | **Backups cannot be restored**. A backup exists but fails at restore time because it was never fully restored or the procedure is unwritten | 2 | 4 | 8 | Moderate | Mitigate | Write a restore runbook and run a full restore drill twice a year | 4 (Low) | [F-10](04-poam.md) | 2026-11-15 |
| R-03 | **Backup decryption key lost**. The offline copies of the key are lost or unreadable, so encrypted vault backups cannot be opened | 2 | 4 | 8 | Moderate | Mitigate | Keep two offline copies and test that the paper copy is readable during the restore drill | 4 (Low) | [F-10](04-poam.md) | 2026-11-15 |
| R-08 | **Theft of the server exposes data**. Someone steals the server or media drive and reads files, because the disks are not encrypted | 2 | 4 | 8 | Moderate | Accept | Accepted for now. Encrypting the boot disk on a server that must restart unattended needs extra setup. Revisit after the second copy exists | 8 (Moderate) | [F-17](04-poam.md) | 2027-04-30 |
| R-16 | **Private network access rules too permissive**. Any device on the private network can reach every service, so one lost device exposes all of them | 2 | 4 | 8 | Moderate | Mitigate | Write access rules that limit each device group to the services it needs | 4 (Low) | [F-25](04-poam.md) | 2026-12-15 |
| R-07 | **DNS outage or unfiltered fallback**. The only filtering resolver fails, so the household loses DNS or falls back to an unfiltered resolver | 3 | 2 | 6 | Moderate | Mitigate | Bring the spare Raspberry Pi back as a second resolver and keep the two in sync | 2 (Low) | [F-14](04-poam.md) | 2026-12-31 |
| R-10 | **LAN traffic in plain HTTP**. Someone on the home network reads or changes traffic to services reached by local name | 2 | 3 | 6 | Moderate | Mitigate | Add internal TLS for local names where practical | 3 (Low) | [F-22](04-poam.md) | 2027-01-31 |
| R-18 | **Stale or incomplete documentation**. Out-of-date documentation leads to wrong decisions, missed reviews, or a recovery that follows the wrong steps | 3 | 2 | 6 | Moderate | Mitigate | Complete the missing documents and hold a first policy review | 4 (Low) | [F-24](04-poam.md) | 2027-01-31 |
| R-13 | **Outside supplier unavailable**. A supplier such as the private network provider or the home automation relay has an outage | 2 | 2 | 4 | Low | Accept | Local access still works. Remote access resumes when the supplier does | 4 (Low) | None | 2027-04-30 |

L is likelihood and I is impact. Target is the score after the planned treatment. Due or review is the target date for a Mitigate item and the review date for an Accept item.

## Accepted risks

A risk is accepted only with a written reason and a review date. No High or Critical risk is accepted.

| ID | Risk | Score | Reason | Review date |
| --- | --- | --- | --- | --- |
| R-08 | Theft of the server exposes data | 8 (Moderate) | Accepted for now. Encrypting the boot disk on a server that must restart unattended needs extra setup. Revisit after the second copy exists | 2027-04-30 |
| R-13 | Outside supplier unavailable | 4 (Low) | Local access still works. Remote access resumes when the supplier does | 2027-04-30 |

## Closed risks

Risk IDs are never reused, so a gap in the numbers is a closed risk.

| ID | Risk | Closed | What was done | Finding |
| --- | --- | --- | --- | --- |
| R-12 | System disk fills up | 2026-10-12 | The system volume was extended using free space already available. Usage fell from 76 percent to 51 percent | [F-19](04-poam.md) |
| R-14 | File sharing exposed more widely than needed | 2026-10-12 | The service was unused, so it was turned off. Files move over SFTP with the SSH key | [F-20](04-poam.md) |
| R-15 | Old device keeps access to the private network | 2026-10-12 | A device offline for months was removed from the private network. The quarterly device review is now policy | [F-21](04-poam.md) |
