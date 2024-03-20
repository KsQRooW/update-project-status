# Update Project Status
GitHub Action to update issue status in Project

# Example

```yaml
name: Project update

on:
  pull_request:
    types: [opened, reopened, converted_to_draft, ready_for_review, synchronize]
  pull_request_review:
    types: [edited, submitted, dismissed]

jobs:
  project:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: ./.github/actions/project
        with:
          project_token: ${{ secrets.PROJECT_TOKEN }}
          pr_action: ${{ github.event.action }}
          pr_state: ${{ github.event.review.state }}
```
