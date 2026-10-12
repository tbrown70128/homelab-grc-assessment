# Assessment method

This is a self-assessment of a small home lab against the NIST Cybersecurity Framework (CSF) 2.0. It follows the same steps a first-line GRC analyst would use: define scope, inventory assets, assess controls against a framework, score risk, and track remediation to closure.

## Standard used

NIST Cybersecurity Framework 2.0 (NIST CSWP 29). Category and subcategory IDs in this repo were checked against NIST's published text on 2026-10-12. The outcome wording in the tables is a short paraphrase for readability. The official wording is in the [NIST publication](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).

Only the subcategories that apply to a household environment were assessed. The rest are out of scope, not failed.

## What this is and is not

| It is | It is not |
| --- | --- |
| A documented review of controls with dated evidence | A certification or an audit report |
| A risk register using one stated scoring method | A claim of formal compliance with any framework |
| A plan of action with owners, dates, and status | A penetration test or a vulnerability scan |

The assessor is also the administrator, so there is no independence. Where a statement could not be backed by a captured command or a document, it is marked as an owner attestation in the [evidence index](05-evidence-index.md).

## Assessment date and cadence

Assessment date: 2026-10-12. Re-assess every six months, and after any major change. Next review: 2027-04-12.

## Control status definitions

| Status | Meaning |
| --- | --- |
| Implemented | The control is in place and there is dated evidence it works |
| Partial | The control exists but has a known weakness, or only covers part of the scope |
| Gap | The control is not in place |

Every Partial or Gap row links to a finding in the [plan of action](04-poam.md).

## Risk scoring

Each risk gets a likelihood score and an impact score from 1 to 5. The risk score is likelihood multiplied by impact.

Likelihood, for this household environment:

| Score | Label | Meaning |
| --- | --- | --- |
| 1 | Rare | Less than once in 10 years |
| 2 | Unlikely | About once in 5 to 10 years |
| 3 | Possible | About once in 2 to 5 years |
| 4 | Likely | About once a year |
| 5 | Almost certain | Several times a year |

Impact:

| Score | Label | Meaning |
| --- | --- | --- |
| 1 | Negligible | Minor inconvenience |
| 2 | Minor | A service is down for hours, nothing is lost |
| 3 | Moderate | A service is down for days, or a small amount of data is lost and can be recovered |
| 4 | Major | Important data is lost, or credentials or private data are exposed |
| 5 | Severe | Irreplaceable data such as family photos is lost, or the password vault is compromised |

Rating bands:

| Score | Rating |
| --- | --- |
| 1 to 4 | Low |
| 5 to 9 | Moderate |
| 10 to 15 | High |
| 16 to 25 | Critical |

Scores are the current score, which already counts the controls in place today. Each risk also has a target score for after its planned treatment is done.

## Risk appetite

- Low appetite for loss of irreplaceable data (family photos, documents) and for compromise of the password vault.
- Moderate appetite for temporary loss of convenience services such as media streaming, recipes, and dashboards.
- Every High or Critical risk needs a treatment plan with a target date.
- A Moderate risk may be accepted with a written reason and a review date.
- A Low risk may be accepted.

## Treatment options

Mitigate (reduce the risk with a control), Accept (keep the risk, with a reason and a review date), Transfer (use a provider or insurance), Avoid (stop the activity).

## Plan of action status values

| Status | Meaning |
| --- | --- |
| Open | Work is planned or in progress |
| Blocked | Work cannot proceed until something else happens, noted in the row |
| Accepted | The risk is knowingly kept, with a reason and a review date |
| Closed | Fixed and verified, with the evidence ID and date |

## Privacy of evidence

Raw captures contain private addresses and names, so they are not published. The evidence index describes what was captured, when, and what it showed. Details that would help an attacker, such as addresses, port numbers, and account names, are left out of this repo on purpose.
