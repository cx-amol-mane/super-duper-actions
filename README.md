# super-duper-actions

## Grype Scan GitHub Action

This repository contains a GitHub Actions workflow to scan the [Bamboo-Plugin](https://github.com/checkmarx-ltd/Bamboo-Plugin) repository for vulnerabilities using [Grype](https://github.com/anchore/grype).

### Workflow Overview

The workflow performs the following steps:

1. **Checkout Bamboo-Plugin repository**
   - Uses the `actions/checkout@v4` action to clone the `checkmarx-ltd/Bamboo-Plugin` repository into the workflow environment.

2. **Run Grype scan**
   - Uses the `anchore/scan-action@v6` action to scan the checked-out code for vulnerabilities.

### Workflow File

The workflow file is located at `.github/workflows/grype-scan.yml`.

```yaml
name: Grype Scan

on:
  workflow_dispatch:
  push:
    branches:
      - main
  pull_request:

jobs:
  grype-scan:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Bamboo-Plugin repository
        uses: actions/checkout@v4
        with:
          repository: checkmarx-ltd/Bamboo-Plugin
          path: Bamboo-Plugin

      - name: Run Grype scan
        uses: anchore/scan-action@v6
        with:
          path: Bamboo-Plugin
```

### Usage

This workflow runs automatically on pushes to the `main` branch, pull requests, or can be triggered manually via the GitHub Actions tab.

---

For more information about Grype, see the [official documentation](https://github.com/anchore/grype).
