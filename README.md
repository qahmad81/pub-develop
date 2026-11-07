# Pub Develop

Pub Develop is a governance protocol for open-source projects on GitHub. It gives application testers and contributor agents a way to participate. Its initial focus is web, PHP, and Python projects, but any project can adopt it. The project owner sets the direction, and the owner's agent evaluates proposals against a published policy. Approved decisions become tasks that contributor agents can claim and implement. Changes go through review and testing before merge.

[Development status](DEVELOPMENT.md) · [Contributors](CONTRIBUTORS.md) · [Installation and updates](INSTALL.md) · [MIT license](LICENSE)

## How to contribute

| Path | What to do |
| --- | --- |
| Try the application | Install it, use it, and open a GitHub issue describing a problem or suggestion and its impact. Your experience using the application is enough. |
| Contribute through your agent | Give your agent the project repository URL and the [contributor prompt](.pub-develop/prompts/contributor.md). After a one-time setup of the appropriate GitHub permissions, it can choose a ready task, work in a fork, and open a pull request. |

## From proposal to merge

1. The owner's agent reviews issues on a schedule and records each decision against the project's goals, impact, evidence, and cost. It can accept a specific part of a proposal. Features that expand the scope go to the [maintainer committee](.pub-develop/committee.md) for a vote.
2. The owner publishes approved tasks to the [task board](.pub-develop/tasks/README.md). Each task has a defined scope, acceptance criteria, and verification steps.
3. The contributor's agent opens a pull request linked to the task. Authorized maintainers or their agents review changes on a schedule. Each maintainer has one vote.
4. Related tasks can be grouped on a protected integration branch with dedicated test tasks. The final pull request is reviewed and the group is tested before merge.
5. The owner's agent records [contribution points](.pub-develop/points.md) using auditable evidence. Points cover reports, ideas, verification, and implementation.

## Adopting the protocol

1. Install the protocol as a development dependency using the [installation guide](INSTALL.md). Set up the project configuration and committee on the protected governance ref. Define the goals, scope boundaries, and IDs of the repository, owner, and reviewers.
2. Set up branch protection and permissions using the [governance policy](.pub-develop/policy.md). Configure the agent runtime to use a trusted governance ref and an owner-approved policy version.
3. Use the [owner agent prompt](.pub-develop/prompts/owner.md) and [reviewer prompt](.pub-develop/prompts/reviewer.md) with your agent scheduler. Start in preview mode and review proposed decisions before enabling writes and merges through controls outside the model.

Protocol version `0.2.0` provides the policy, prompts, and templates. Automation requires implementing the runner, connecting the scheduler and GitHub APIs, enforcing the merge gate, and isolating code execution. [Current implementation status](DEVELOPMENT.md)
