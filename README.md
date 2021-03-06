# Enforce PR label

Enforce choosing label before merging PR. Usefull for generating automatic changelog and release notes with `github-release-notes`

## Example usage
Create `.github/workflows/enforce-labels.yml` containing:

```yml
name: Require PR label

on:
  pull_request:
    types: [opened, labeled, unlabeled]

jobs:
  require-label:
    runs-on: ubuntu-latest
    steps:
    - uses: yogevbd/enforce-label-action@2.0.0
      env:
        REQUIRED_LABELS_ANY: "bug,enhancement,wontfix"
        REQUIRED_LABELS_ALL: "required"
        BANNED_LABELS: "banned"

```
**`REQUIRED_LABELS_ANY`**: Force PR's to have at least one label, excepts multiple labels seperated by a comma.  
**`REQUIRED_LABELS_ALL`**: Force PR's to have all labels, excepts multiple labels seperated by a comma.  
**`BANNED_LABELS`**: Prevent PR's with those labels to be merged, excepts multiple labels seperated by a comma.  
