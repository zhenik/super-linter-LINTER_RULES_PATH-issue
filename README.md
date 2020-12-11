# Issue with env `LINTER_RULES_PATH`

## Problem

Overriding env var `LINTER_RULES_PATH` (`.github/linters`)

Does not catch changes when I try override `LINTER_RULES_PATH`
[not working] But expected to fail with new `.tflint.hcl` rules
```bash
docker run -it \
    -v "${PWD}:/tmp/lint" \
    -e "RUN_LOCAL=true" \
    -e "DEFAULT_WORKSPACE=/tmp/lint" \
    -e "LINTER_RULES_PATH=/tmp/lint/custom/linters" \
    github/super-linter:v3
```

[working - using default] Fail as expected
```bash
docker run -it \
    -v "${PWD}:/tmp/lint" \
    -e "RUN_LOCAL=true" \
    -e "DEFAULT_WORKSPACE=/tmp/lint" \
    github/super-linter:v3
```

add for debug `--entrypoint /bin/bash \`
