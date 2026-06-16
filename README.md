# Grounded Consumption Contracts Reviewer Artifact

This package accompanies the TODS submission "Grounded Consumption Contracts:
Construction-Time Soundness for Generated Claims over Governed Data." It
contains the anonymized release files needed to reproduce the paper's
claim-disposition tables, governance-drop witness, G1-G5 soundness-test matrix,
replay summary, and external grounding reachability aggregates.

## Quick Start

```bash
python3 reproduce.py
```

The script uses only the Python standard library, reads only files shipped in
this directory, and writes:

```text
results/reproduced_results.json
```

No database, network access, environment variables, private access material, or
non-standard packages are required.

## What Is Included

- `contracts/grounding_contracts.sql`: the anonymized three-table claim
  grounding contract: claim registry, claim-to-evidence binding, and coverage
  ledger.
- `data/table_manifest.csv`: released aggregate row counts for the 19-table
  production snapshot, totaling 10,141 rows.
- `data/claim_dispositions.csv`: 121,760 anonymized surfaced-claim rows with
  sequential opaque claim, snapshot, and item identifiers.
- `data/claim_field_manifest.csv`: field-level claim counts that close to the
  same 121,760 total.
- `data/disposition_summary.json`: pre-gate provenance gap, post-gate
  dispositions, evidence tiers, and operating points.
- `data/assertion_specificity_matrix.json`: G1-G5 perturbation matrix.
- `data/replay_summary.json`: version-pin completeness, typed replay, and
  score-only ranking auditability boundary.
- `data/upstream_summary.json`: upstream clock and funnel-integrity aggregates.
- `data/external_grounding_summary.json`: aggregate reachability counts for an
  independent product-knowledge source.
- `data/outcome_anchor.csv`: aspect-level outcome-anchor aggregates.

## Expected Headline Checks

Running `python3 reproduce.py` should reproduce:

- 19 released snapshot tables with 10,141 aggregate rows.
- 121,760 surfaced claims.
- 121,760 / 121,760 claims with empty pre-gate provenance.
- 121,760 / 121,760 claims with null pre-gate recorded-at timestamp.
- Post-gate dispositions: 24,972 grounded, 79,770 caveat, 11,460
  degrade-derived, and 5,558 degrade-unmapped.
- 104,742 / 121,760 = 86.02% binding-or-caveat coverage.
- 1,130 / 1,130 funnel monotonicity.
- A clean G1-G5 specificity diagonal with no cross-firing.
- 100% same-source typed replay over the released claim-disposition function.
- Score-only ranking-order reproducibility for 844 / 1,130 snapshots = 74.69%,
  reported as an auditability boundary rather than a full ranking replay claim.

## Reproducibility Boundary

The package reproduces the released aggregate and claim-level evidence from
sanitized tables. It does not include the private production database, raw
product records, prices, customer or order identifiers, local snapshot mirrors,
internal hosts, private access material, authoring history, cover letters, or review-process
notes.

The released identifiers are sequential opaque IDs. Product names, brand names,
SKU values, organization names, author identities, and local machine paths have
been removed from reviewer-facing files.
