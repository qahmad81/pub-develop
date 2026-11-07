# Contribution points

Points recognize participation based on verified impact. The total can show a participant's reputation, and the owner may consult it when deciding whether to offer an optional reward. The protocol calculates points. A points award carries no entitlement to payment or revenue.

## Scoring rules · 0.1.0

| Contribution | Points | Award condition |
| --- | ---: | --- |
| `reproduced_bug` | 3 | A report makes an in-scope bug reproducible, and the report and evidence are accepted. |
| `accepted_idea` | 2 | The project accepts an idea in whole or in part and creates a task for it. Award once per original idea. |
| `verified_test` | 2 | An independent test uncovers a new defect or covers a previously unverified acceptance criterion, and the project accepts the result. |
| `merged_task` | 5 | A task, including a test task, reaches the main branch. Award once per task. |

1. Use the contributor's verified numeric GitHub ID. Credit an agent's work to the account it represents when the relationship is verified. Leave attribution pending when verification is unavailable. Credit each task to one verified account. Record supporting contributions separately when they qualify.
2. Assign one category to each piece of evidence. If multiple categories cover the same impact, use the highest value. One person can earn points for both a report and an implementation when each has independent evidence. Award an original report or idea once, even if multiple issues describe it. New evidence from a duplicate issue may qualify as `verified_test`.
3. The owner's agent determines eligibility from documented decisions and evidence. The runner calculates the points from the contribution category and rules version and enforces uniqueness before inserting an award. Claims, comment volume, opening a pull request, and repeated identical tests earn no points. A `merged_task` award waits until the task reaches main, including tasks previously merged into an integration branch.
4. The owner reviews objections and attribution disputes. Add one reversing entry to cancel the original, then add a replacement entry if a valid award remains. Include the reason and audit references. Keep prior entries and calculate the balance by summing signed values. When weights change, apply the new rule version to future awards.

## Ledger

Store `entry_id`, `repository_id`, `account_id`, `kind`, `subject_id`, `points`, `evidence`, `policy_version`, `recorded_at`, and `recorded_by` for each entry. A reversing entry also stores `reverses_entry_id`. The `subject_id` identifies the original report or idea, a task, or an approved verification of an independent result. Each `(repository_id, kind, subject_id)` tuple can have one active award. When reassigning credit, link the replacement to the reversed entry and record the correction atomically. Keep the ledger in protected governance storage. A public summary can include balances and public evidence while omitting secrets and contact details.

**Example.** Award 3 points to the person who supplies reproduction steps for a bug, 5 to the person whose fix reaches main, and 2 to a tester who verifies an additional approved case. Record each contribution when it meets its own award condition.
