# Backup and recovery policy

| | |
| --- | --- |
| Owner | Terence, administrator |
| Version | 1.0, effective 2026-10-12 |
| Next review | 2027-04-12 |
| CSF 2.0 | PR.DS-01, PR.DS-11, PR.IR-03, RC.RP-03, RC.RP-05 |

## Purpose

Make sure the household can get its important data back after a failure, a mistake, or a theft.

## Scope

The password vault, family photos, documents and synced files, budgeting data, Home Assistant, and service configuration. The media library is replaceable and is not backed up.

## Recovery targets

| Tier | Data | Most data loss allowed | Time to restore |
| --- | --- | --- | --- |
| 1 | Password vault | 24 hours | 1 day |
| 1 | Family photos, documents and synced files, budget data | 24 hours | 7 days |
| 2 | Home Assistant, service configuration | 7 days | 7 days |
| 3 | Media library | None, replaceable | Best effort |

## Policy

1. **3-2-1 for Tier 1.** Keep three copies on two kinds of storage, with one copy away from the house.
2. **Automatic.** Backups run on a schedule. Nothing depends on remembering to run one.
3. **Encrypted.** Any backup that contains credentials or key material is encrypted before it is stored. The decryption key is never stored on the server. It is kept offline in two separate places, and neither one depends on the password manager.
4. **Checked.** Each backup is checked for integrity when it is made.
5. **Retention.** Keep 14 days of daily backups for the password vault.
6. **Restore drill.** Twice a year, restore the password vault into a scratch service from an encrypted backup, using the key from its offline copy. Record the date and the result. Repeat after any change to the backup method.
7. **Runbook.** A written restore procedure exists for each Tier 1 item and says what to do first, what to check, and how to confirm the restored service is correct.
8. **Key custody check.** Each year, confirm both offline copies of the key are present and readable.
9. **Rotation and cleanup.** If a backup key is exposed, replace it, make a new backup, and delete backups made with the old key and any unencrypted copies.

## Where the lab stands today

| Statement | Status | Finding |
| --- | --- | --- |
| 1 3-2-1 for Tier 1 | Not met. Photos and files exist in one place. The vault has two copies in the same machine | [F-09](../docs/04-poam.md) |
| 2 Automatic | Met for the vault and Home Assistant | |
| 3 Encrypted | Met for the vault. Key kept offline in two places | |
| 4 Checked | Met for the vault | |
| 5 Retention | Met. Retention history restarted on 2026-10-12 when the old unencrypted archives were deleted | |
| 6 Restore drill | Partly met. A decryption test passed on 2026-10-12. No full restore yet | [F-10](../docs/04-poam.md) |
| 7 Runbook | Not yet written | [F-10](../docs/04-poam.md) |
| 8 Key custody check | First check due 2027-10-12 | |
| 9 Rotation and cleanup | Met. Done on 2026-10-12 after a partial exposure | |

Home Assistant backs up to cloud storage. Adding a second location is tracked in the [roadmap](https://github.com/tbrown70128/homelab-docs/blob/main/docs/roadmap.md).
