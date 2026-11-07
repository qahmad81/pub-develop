# Pub Develop development status

**Report snapshot** 2026-11-07 · **Release scope** Governance protocol and tools for running it on GitHub.

| Metric | Result |
| --- | ---: |
| Core objective completion | **60%** (12 of 20 effort units) |
| Approved secondary scope relative to core scope | **0%** (0 of 20 effort units) |

## Core objectives

| Objective | Weight | Completed | Status and evidence |
| --- | ---: | ---: | --- |
| C01 · Triage issues and turn accepted proposals into tasks | 3 | 3 | Triage rules and the task template are ready. [Policy](.pub-develop/policy.md) · [Task board](.pub-develop/tasks/README.md) |
| C02 · Document agent permissions, review, and integration | 3 | 3 | Prompts, approval requirements, and integration branch rules are documented. [Policy](.pub-develop/policy.md) |
| C03 · Define voting, reputation, nominations, and reports | 4 | 4 | Governance procedures and reporting formulas are documented. [Committee](.pub-develop/committee.md) · [Contributors](CONTRIBUTORS.md) |
| C04 · Distribute the protocol as a development dependency | 2 | 2 | The Composer package definition and PHP and Python instructions are ready. [Installation](INSTALL.md) |
| C05 · Run triage, review, and voting cycles and generate reports | 4 | 0 | Requires implementing the runner and connecting it to GitHub. |
| C06 · Enforce protection and merges and verify them in a test repository | 4 | 0 | Requires implementing the merge gate and testing the controls. |

## Secondary objectives

This snapshot contains no approved secondary objectives or recorded votes. When proposals are open, list their issue links, effort weights, and voting deadlines here.

## Updating this report

- Record each objective's ID, category, and positive weight on a shared effort scale. Break it into verifiable outcomes whose weights add up to the objective weight. Count completed outcomes with dated evidence. A completed document counts toward a documentation objective. An operational objective requires evidence of a working implementation.
- **Core completion** = `100 × completed core outcome weight ÷ total approved core objective weight`. **Secondary scope** = `100 × total approved secondary objective weight ÷ total approved core objective weight`. The denominator includes completed and remaining core work, and the secondary numerator includes completed and remaining secondary work. Secondary scope can exceed 100%. Show “Not calculated” when the denominator is zero.
- Exclude pending and rejected proposals and cancelled objectives. A committee vote fixes a secondary objective's scope and weight before it enters the calculation. Record changes to weights, outcomes, or categories with reasons in the governance log, and generate the report from a single dated snapshot. The weights above are initial effort estimates.
