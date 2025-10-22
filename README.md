# sonarqube-status-comment
Get SonarQube Quality Gate status and write it as a comment in a Pull Request.

# SonarQube Quality Gate Status Comment Action

This GitHub composite action retrieves the SonarQube Quality Gate status for a pull request and posts it as a comment. It also annotates the PR with issue findings from SonarQube.

## 📦 Features

- Validates that the workflow is triggered by a pull request.
- Retrieves Quality Gate status from SonarQube.
- Posts a formatted comment with gate status and metrics.
- Updates existing comments or creates new ones.
- Annotates PR with SonarQube issues using GitHub annotations.

##  🚀 Usage:

```yaml
jobs:
  sonar-comment:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: SonarQube Quality Gate status comment
        uses: telia-actions/sonarqube-pr-comment@v1
        with:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
          SONAR_HOST_URL: ${{ vars.SONAR_HOST_URL }}
          SONAR_PROJECT_KEY: ${{ vars.SONAR_PROJECT_KEY }}
          GITHUB_EVENT_NUMBER: ${{ github.event.pull_request.number }}
```

## 🧾 Inputs

| Name | Description | Required |
|------|-------------|----------|
| `SONAR_TOKEN` | SonarQube token for API access | ✅ Yes |
| `SONAR_HOST_URL` | SonarQube server URL | ✅ Yes |
| `SONAR_PROJECT_KEY` | SonarQube project key | ✅ Yes |
| `GITHUB_EVENT_NUMBER` | GitHub Pull Request number | ✅ Yes |