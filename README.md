# cz-conventional-changelog-with-issue-id

Status:
[![npm version](https://img.shields.io/npm/v/cz-conventional-changelog.svg?style=flat-square)](https://www.npmjs.org/package/cz-conventional-changelog-with-issue-id)
[![npm downloads](https://img.shields.io/npm/dm/cz-conventional-changelog.svg?style=flat-square)](http://npm-stat.com/charts.html?package=cz-conventional-changelog-with-issue-id&from=2015-08-01)

Part of the [commitizen](https://github.com/commitizen/cz-cli) family. Prompts for [conventional changelog](https://github.com/conventional-changelog/conventional-changelog) standard.

Makes specifying an issue id mandatory. The desired commit types can be
configured to make the issue id optional.

## Configuration

### package.json

Like commitizen, you specify the configuration of cz-conventional-changelog through the package.json's `config.commitizen` key.

```json5
{
// ...  default values
    "config": {
        "commitizen": {
            "path": "./node_modules/cz-conventional-changelog",
            "disableScopeLowerCase": false,
            "disableSubjectLowerCase": false,
            "maxHeaderWidth": 100,
            "maxLineWidth": 100,
            "defaultType": "",
            "defaultScope": "",
            "defaultSubject": "",
            "defaultBody": "",
            "defaultIssues": "",
            "issuePrefix": "#",
            "typesWithOptionalIssueIds": ["chore", "docs", "revert"],
            "types": {
              ...
              "feat": {
                "description": "A new feature",
                "title": "Features"
              },
              ...
            }
        }
    }
// ...
}
```

### Environment variables

The following environment variables can be used to override any default configuration or package.json based configuration.

| Environment variable          | package.json              | Default                     | Description                                                                               |
| ----------------------------- | ------------------------- | --------------------------- | ----------------------------------------------------------------------------------------- |
| CZ_MAX_HEADER_WIDTH           | maxHeaderWidth            | 100                         | This limits how long a commit message head can be.                                        |
| CZ_MAX_LINE_WIDTH             | maxLineWidth              | 100                         | Commit message bodies are automatically wrapped. This decides how long the lines will be. |
| CZ_TYPE                       | defaultType               | undefined                   | The default type.                                                                         |
| CZ_SCOPE                      | defaultScope              | undefined                   | The default scope.                                                                        |
| DISABLE_SCOPE_LOWERCASE       | disableScopeLowerCase     | false                       | Decides if converting given scope to lowercase should be prevented.                       |
| DISABLE_SUBJECT_LOWERCASE     | disableSubjectLowerCase   | false                       | Decides of converting given subjest to lowercase should be prevented.                     |
| CZ_SUBJECT                    | defaultSubject            | undefined                   | A default subject.                                                                        |
| CZ_BODY                       | defaultBody               | undefined                   | A default body.                                                                           |
| CZ_ISSUES                     | defaultIssues             | undefined                   | Default issue(s).                                                                         |
| CZ_ISSUE_PREFIX               | issuePrefix               | #                           | The issue prefix.                                                                         |
| CZ_TYPES_WITH_ISSUES_OPTIONAL | typesWithOptionalIssueIds | ["chore", "docs", "revert"] | The commit types that may be made without associated issue id(s).                         |

### Commitlint

If using the [commitlint](https://github.com/conventional-changelog/commitlint) js library, the "maxHeaderWidth" configuration property will default to the configuration of the "header-max-length" rule instead of the hard coded value of 100. This can be ovewritten by setting the 'maxHeaderWidth' configuration in package.json or the CZ_MAX_HEADER_WIDTH environment variable.
