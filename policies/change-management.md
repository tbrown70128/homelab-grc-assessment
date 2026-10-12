# Change management policy

| | |
| --- | --- |
| Owner | Terence, administrator |
| Version | 1.0, effective 2026-10-12 |
| Next review | 2027-04-12 |
| CSF 2.0 | PR.PS-01, PR.PS-02, ID.RA-07 |

## Purpose

Keep the lab stable and recoverable by making changes deliberately, one at a time, and with a way back.

## Scope

Any change to the server, its services, the virtual machine, the network equipment, firewall rules, remote access, and backup jobs.

## Policy

1. **Defined in files.** Every service is defined in a compose file. Changes are made in the file, not by hand on a running container.
2. **Pinned versions.** Container images use an exact version, not `latest` or another floating tag. Supporting images may use a major version.
3. **One change at a time.** Make one change, check it, then make the next. This also applies while troubleshooting.
4. **Prepare a way back.** Before a change, keep a copy of the file being changed. Before a change to a service that holds data, make sure a recent backup exists.
5. **Check after.** After a change, confirm the service works, its data is intact, and monitoring is green.
6. **Check ports first.** Before adding a service or a published port, check the reserved ports table.
7. **Record it.** Write a decision record for any change to remote access, authentication, or the network design. Write an incident review for any outage.
8. **Updates.** Review updates for every service once a month. Update one service at a time, in this order: low-risk first, the password manager and files last.
9. **Emergency changes.** In an outage, a change may be made first and recorded afterward, within seven days.
10. **Exceptions and risk.** A change that adds risk needs the risk added to the register, with a treatment and a review date.

## Where the lab stands today

| Statement | Status | Finding |
| --- | --- | --- |
| 1 Defined in files | Met | |
| 2 Pinned versions | Met on 2026-10-12 | |
| 3 One change at a time | Met | |
| 4 Prepare a way back | Met | |
| 5 Check after | Met | |
| 6 Check ports first | Met | |
| 7 Record it | Met. Decision records and incident reviews are in the lab docs | |
| 8 Updates | Not yet scheduled. A monthly review starts by 2026-11-15 | [F-18](../docs/04-poam.md) |
| 9 Emergency changes | No emergency changes recorded to date | |
| 10 Exceptions and risk | Met for this assessment | |
