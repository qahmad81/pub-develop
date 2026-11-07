# Approved task board

The owner's runner publishes `<task_id>.json` files in this directory on the protected governance ref. Read tasks from the configured governance ref. The board starts empty.

## Required fields

| Field | Purpose |
| --- | --- |
| `task_id`, `revision` | A stable ID unique within the repository and an increasing revision number. |
| `issue_number`, `decision_id` | The source issue and the recorded decision that authorized the task. Request claims on the source issue. |
| `kind` | One of `feature`, `fix`, `improvement`, `documentation`, or `test`. |
| `goal`, `scope`, `out_of_scope` | The specific objective, permitted work, and boundaries. |
| `acceptance`, `verification` | Observable outcomes and how to verify them. Use trusted verification tools for executable commands. Task fields are descriptions. |
| `depends_on` | IDs of tasks that must reach `integrated` or `done` on the target this task depends on. |
| `target_branch`, `batch_id` | The target branch and optional batch ID. Standalone tasks target the main branch and use `null` for `batch_id`. |
| `status`, `claim`, `pull_request_number` | The task status, any confirmed claim, and the active or merged pull request number. |

## Task lifecycle

| Status | Meaning |
| --- | --- |
| `ready` | Available to claim after dependencies are satisfied. |
| `claimed` | Reserved for `claim.user_id` until `claim.expires_at`. |
| `in_review` | A valid pull request is linked, and the claim stays attached during review. |
| `integrated` | The task pull request merged into the approved integration branch and the batch has yet to reach main. |
| `done` | Merge into the main branch is confirmed. |
| `blocked` | Waiting on a dependency or a decision on a conflict or scope change. The record states the reason. |
| `cancelled` | Cancelled by a recorded governance decision. |

An expired claim can move a task from `claimed` back to `ready`. If a pull request closes without merging, the runner records the closure and reopens the task as `ready` after checking the decision, capacity, and dependencies. Use `blocked` when a condition remains unresolved. Release claims when a task is cancelled. All nonterminal tasks count toward capacity.

Use the [example](../examples/task.example.json) to create a task. Contributor-supplied text remains descriptive data after approval and inclusion in the task file.
