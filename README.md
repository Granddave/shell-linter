# Shell Linter

[![Release](https://img.shields.io/github/release/azohra/shell-linter.svg)](https://github.com/azohra/shell-linter/releases)
[![Marketplace](https://img.shields.io/badge/GitHub-Marketplace-red.svg)](https://github.com/marketplace/actions/shell-linter)
[![Actions Status](https://github.com/azohra/shell-linter/workflows/CI-workflow/badge.svg)](https://github.com/azohra/shell-linter/actions?query=branch%3Adevelop)


A GitHub Action that performs static analysis for shell scripts using [ShellCheck](https://github.com/koalaman/shellcheck).

![](docs/images/preview.png)

<br>

# Usage

Shell Linter can perform static analysis in various ways. You can use it to lint all the shell scripts in your project or lint a specific file or folder using the `path` parameter. Specific use cases are shown below:

Run static analysis for all shell scripts in your repository:
```yml
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
      - uses: actions/checkout@v1
      - name: Run Shellcheck
        uses: azohra/shell-linter@latest
```

Run static analysis for a single shell script:
```yml
      - name: Run Shellcheck
        uses: azohra/shell-linter@latest
        with:
          path: "setup.sh"
```

Run static analysis for multiple shell scripts **with or without** extension:
```yml
      - name: Run Shellcheck
        uses: azohra/shell-linter@latest
        with:
          path: "setup,deploy.sh"
```

Run static analysis for all the shell scripts in a folder:
```yml
      - name: Run Shellcheck
        uses: azohra/shell-linter@latest
        with:
          path: "src"
```

Run static analysis using a **wildcard** path:
```yml
      - name: Run Shellcheck
        uses: azohra/shell-linter@latest
        with:
          path: "src/*.sh"
```

Run static analysis for all the shell scripts and only report issues with error severity while excluding specific issues:
```yml
      - name: Run Shellcheck
        uses: azohra/shell-linter@latest
        with:
          path: "src/*.sh"
          severity: "error"
          exclude: "SC1068,SC1066"
```

Run analysis by using a specific version of Shell Linter:
```yml
      - name: Run Shellcheck
        uses: azohra/shell-linter@v0.5.0
```

# Input

### `path`

Optional. Execute lint check on a specific file or folder. Default: `.`

### `severity`

Optional. Specify minimum severity of errors to consider [style, info, warning, error]. Default: `style`

### `exclude`

Optional. Specify shellcheck issues to exclude during scan. For more information refer to [Checks](https://github.com/koalaman/shellcheck/wiki/Checks). Default: scan all issues.

# License
This software is available as open source under the terms of the MIT License.
