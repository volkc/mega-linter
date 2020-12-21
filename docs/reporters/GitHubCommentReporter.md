# GitHub Comment Reporter

Posts Mega-Linter results summary in the comments of the related pull request (if existing)

## Usage

Click on hyperlinks to access detailed logs

![Screenshot](../assets/images/GitHubCommentReporter.jpg)

## Configuration

| Variable | Description | Default value |
| ----------------- | -------------- | :--------------: |
| GITHUB_COMMENT_REPORTER | Activates/deactivates reporter | true |
| GITHUB_API_URL | URL where the github API can be reached | https://api.github.com |
| GITHUB_ACTION_RUN_URL | URL pointing to the CI/CD system where the megalinter logs can be viewed. | Github Action page |
| GITHUB_ACTION_RUN_URL_DESC | Overwrites the action run description, in case another CI/CD system (e.g. Jenkins) is used. | "Github Action page" |
