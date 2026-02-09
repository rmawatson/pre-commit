[![build status](https://github.com/pre-commit/pre-commit/actions/workflows/main.yml/badge.svg)](https://github.com/pre-commit/pre-commit/actions/workflows/main.yml)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/pre-commit/pre-commit/main.svg)](https://results.pre-commit.ci/latest/github/pre-commit/pre-commit/main)

## This fork adds --tool argument to allow invocation of hooks as tools from the command line.

[[Original PR]](https://github.com/pre-commit/pre-commit/pull/3618)

## Using pre-commit hooks as terminal tools

By default, pre-commit only allows invoking a hook with its preconfigured arguments:
```bash
pre-commit run example-hook
```

Passing different arguments to different invocations requires defining each permutation as a separate entry in `.pre-commit-config.yaml` with specific `args: [...]`. This doesn't support using hooks as general-purpose tools with dynamic arguments.

### The `--tool` flag

When `--tool` is used:

- `allow_all_files=true` is implied
- The hook must be exposed with `stages: ["manual"]`
- Arbitrary arguments can be passed after `--`

### Usage
```bash
pre-commit run <hook-id> --tool -- [arguments...]
```

### Example
```bash
pre-commit run example-hook --tool -- --arg1 --arg2=4
```

This invokes `example-hook` with `--arg1` and `--arg2=4` passed directly to the underlying tool, without needing a predefined entry for each argument combination.

## pre-commit

A framework for managing and maintaining multi-language pre-commit hooks.

For more information see: https://pre-commit.com/
