# Incident response policy

| | |
| --- | --- |
| Owner | Terence, administrator |
| Version | 1.0, effective 2026-10-12 |
| Next review | 2027-04-12 |
| CSF 2.0 | RS.MA-01, RS.AN-03, RC.RP-01, ID.IM-03, ID.IM-04 |

## Purpose

Respond to problems in a calm, consistent way, recover quickly, and learn from each one.

## What counts as an incident

Anything that makes a service unavailable for longer than expected, exposes or may expose data or credentials, or damages data. A false alarm that was checked and ruled out is recorded in one line.

## Severity

| Level | Examples | Response |
| --- | --- | --- |
| 1 Severe | Password vault or an account may be compromised. Irreplaceable data lost | Act immediately. Contain first |
| 2 Major | A core service is down for more than a day, such as DNS, files, photos, or remote access | Act the same day |
| 3 Minor | One convenience service is down. A brief outage | Fix when practical |

## Steps

1. **Notice and declare.** Note the time and what was seen. Decide the level.
2. **Contain.** Stop the problem from growing. Examples: take a service off the network, disable an account, remove a device from the private network.
3. **Preserve.** Save the logs and the state before changing anything, so the cause can be found.
4. **Understand.** Find out what happened, what was affected, and the root cause.
5. **Recover.** Restore from a backup if needed, check the restored data, and confirm monitoring is green.
6. **Replace credentials.** If any password, key, or token may have been exposed, replace it and revoke the old one. Delete any copies made with it.
7. **Tell the household.** Say what happened, what is affected, and what they need to do, such as a new password.
8. **Review.** Within seven days, write a blameless review using the template in the lab docs: timeline, root cause, what worked, what did not, and the changes made. Add any new risk to the register and any new work to the plan of action.

## Roles

One administrator carries every role. The household is told for Level 1 and Level 2 incidents.

## Exercise

Run a short tabletop exercise once a year. Pick a scenario, such as a lost laptop with an SSH key, walk through the steps, and note what was missing.

## Where the lab stands today

| Statement | Status | Finding |
| --- | --- | --- |
| Reviews for real incidents | Met. Several written, with root cause and fixes | |
| Replacing exposed credentials | Met. A key was replaced on 2026-10-12 after a partial exposure on screen | |
| Tabletop exercise | Not yet done. First one due 2026-11-15 | [F-10](../docs/04-poam.md) |
| Restore as part of recovery | Partly met. No full restore drill yet | [F-10](../docs/04-poam.md) |

Past incident reviews are in the [lab docs](https://github.com/tbrown70128/homelab-docs/tree/main/docs/incidents).
