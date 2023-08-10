# github_actions
Reusable Github Actions

### Table of Content
* [Trivy secret scan call](#trivy-secret-scan-call)

# Trivy secret scan call
```yml
name: Trivy secret scan call
on:
  push:
    branches:
    - main
  pull_request:
  workflow_dispatch:

jobs:
  trivy_secret_module_call:
    uses: NadavOps/github_actions/.github/workflows/trivy_fs_secret_scan.yml@main
```
