# Access control policy

| | |
| --- | --- |
| Owner | Terence, administrator |
| Version | 1.0, effective 2026-10-12 |
| Next review | 2027-04-12 |
| CSF 2.0 | PR.AA-01, PR.AA-03, PR.AA-05 |

## Purpose

Make sure only the right people and devices can reach the lab, and that each one can reach only what it needs.

## Scope

All services, the lab server, the network equipment, and the machines used to administer them. Household members who use the services are covered by the account rules.

## Policy

1. **Unique accounts.** Every person has their own login on each service. Shared logins are not used.
2. **Least privilege.** New accounts are not administrators. Administrator rights are given only to the administrator. Integrations use view-only or per-service credentials.
3. **Strong sign-in.** Passwords are generated and stored in the password manager. Two-factor authentication is turned on for every service that supports it, starting with the password manager, files, photos, and budgeting.
4. **Administrative access.** SSH to the server uses keys only. Password login is off. Private keys stay on the device that created them and are protected with a passphrase, unless an exception is recorded below.
5. **Remote access.** Remote access uses the private network or the home automation relay. No router port forwards are opened. Any new way in needs a decision record first.
6. **Network and tool access.** Access rules on the private network limit each device group to the services it needs.
7. **Container control.** No container is given control of Docker. If a tool must read container status, it uses a read-only filtering proxy.
8. **Joiners and leavers.** When a household member leaves, their accounts are disabled the same day. When a device is lost or retired, it is removed from the private network and from the SSH authorized keys the same day.
9. **Access review.** Every quarter, review the private network device list, SSH authorized keys, and the user list of each service. Remove anything not in use.
10. **Credential exposure.** If a password, key, or token is shown or sent where it should not be, treat it as compromised and replace it. Follow the [incident response policy](incident-response.md).

## Exceptions

An exception needs a reason, a risk rating, and a review date. None are recorded today.

## Where the lab stands today

| Statement | Status | Finding |
| --- | --- | --- |
| 1 Unique accounts | Met | |
| 2 Least privilege | Met. The unused file sharing service was turned off | |
| 3 Strong sign-in | Partly met. Two-factor is not on every service | [F-11](../docs/04-poam.md) |
| 4 Administrative access | Met for key-only SSH. Passphrase on the laptop key to be confirmed | [F-27](../docs/04-poam.md) |
| 5 Remote access | Met | |
| 6 Network and tool access | Not yet met. Rules are permissive | [F-25](../docs/04-poam.md) |
| 7 Container control | Met | |
| 8 Joiners and leavers | Met. The one stale device was removed on 2026-10-12 | |
| 9 Access review | Not yet started. First review due 2026-12-31 | [F-24](../docs/04-poam.md) |
| 10 Credential exposure | Met. One key was replaced after a partial exposure | |
