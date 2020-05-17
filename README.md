# Action Stardust

[![actions-workflow-lint][actions-workflow-lint-badge]][actions-workflow-lint]
[![release][release-badge]][release]

Run [micnncim/stardust](https://github.com/micnncim/stardust) as a GitHub Action.

## Inputs

|       NAME        |                              DESCRIPTION                              |   TYPE   | REQUIRED | DEFAULT |
| ----------------- | --------------------------------------------------------------------- | -------- | -------- | ------- |
| `github_token`    | A GitHub token.                                                       | `string` | `true`   | `N/A`   |
| `github_username` | A GitHub username.                                                    | `string` | `true`   | `N/A`   |
| `interval`        | A interval of reports. Must be in the form of `\d+[hms]` like `168h`. | `string` | `true`   | `N/A`   |
| `slack_enabled`   | Whether Slack is enabled as a reporter.                               | `bool`   | `false`  | `N/A`   |
| `slack_token`     | A Slack token.                                                        | `string` | `false`  | `N/A`   |
| `slack_channel`   | A Slack channel.                                                      | `string` | `false`  | `N/A`   |
| `log_level`       | A log level.                                                          | `string` | `false`  | `info`  |

## Example

```yaml
name: Stardust

on:
  schedule:
    - cron: "0 9 * * 0" # At 09:00 on Sunday

jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - uses: micnncim/action-stardust@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          github_username: <GITHUB_USERNAME>
          interval: 168h # 1 week
          slack_enabled: true
          slack_token: ${{ secrets.SLACK_TOKEN }}
          slack_channel: <SLACK_CHANNEL>
```

<!-- badge links -->

[actions-workflow-lint]: https://github.com/micnncim/action-stardust/actions?query=workflow%3ALint
[actions-workflow-lint-badge]: https://img.shields.io/github/workflow/status/micnncim/action-stardust/Lint?label=Lint&style=for-the-badge&logo=github

[release]: https://github.com/micnncim/action-stardust/releases
[release-badge]: https://img.shields.io/github/v/release/micnncim/action-stardust?style=for-the-badge&logo=github
