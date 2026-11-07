# Installing and updating Pub Develop

Pub Develop focuses on web, PHP, and Python projects. The agent reads the documentation from the approved package version and reads each project's configuration, tasks, and decisions from that project's governance ref. Each project keeps its own records and reports. Protocol files live inside the installed dependency.

## PHP and Composer

Run these commands from the adopting project's root. This example uses the GitHub repository directly as a VCS source.

```sh
composer config repositories.pub-develop vcs https://github.com/qahmad81/pub-develop.git
composer require --dev qahmad81/pub-develop:~0.2.0
```

Composer installs the package to `vendor/qahmad81/pub-develop/` by default. Track `composer.json` and `composer.lock` in Git and keep `vendor/` out of version control. `composer install` installs the locked version. `composer install --no-dev` excludes the package from production deployments. To update only this dependency, run `composer update qahmad81/pub-develop` and review the `composer.lock` diff and policy version before approving the update for agents. Running `composer update` without a package updates dependencies within their configured constraints. [Composer vendor directory](https://getcomposer.org/doc/06-config.md#vendor-dir) · [Composer commands](https://getcomposer.org/doc/03-cli.md#update-u-upgrade) · [VCS repositories](https://getcomposer.org/doc/05-repositories.md#vcs)

## Python and other web projects

Use a separate Git checkout in a local tools directory excluded from Git, or in the agent runner's workspace. From the project root, add `/.tools/pub-develop/` to the project's `.gitignore`, then run the following command.

```sh
git clone --branch v0.2.2 --depth 1 https://github.com/qahmad81/pub-develop.git .tools/pub-develop
```

Pin the approved version and commit SHA in the project's development configuration. To update, fetch and review the new tag before changing the approved ref. Projects can also use the Composer setup if Composer is available in their development environment.

## Project-specific files

- Set up `.pub-develop/project.json` and `.pub-develop/committee.json` on the protected governance ref using the [project template](.pub-develop/project.example.json) and [committee template](.pub-develop/committee.example.json). Create `.pub-develop/tasks/` on the same ref for actual tasks using the [task format](.pub-develop/tasks/README.md). The optional GitHub issue form goes in `.github/ISSUE_TEMPLATE/`.
- Generate `DEVELOPMENT.md` and `CONTRIBUTORS.md` from your project's data. Use the [development report](DEVELOPMENT.md) and [contributor report](CONTRIBUTORS.md) as examples. Keep private professional notes outside the public reports.
- Pin the package path and approved policy version in the runner's trusted configuration. Review updates in `preview` mode before activating them. The package distributes documentation and templates. Scheduled execution and enforcement require a runner and merge gate.
