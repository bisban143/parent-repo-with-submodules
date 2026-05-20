# Parent Repository with Submodules

This repository demonstrates Git submodules by linking to multiple branches across different repositories.

## Submodules

This repository contains 4 submodules:

### 1. repo1-java21
- **Repository**: `bisban143/Repo1_for_blitzy_submod_test`
- **Branch**: `main`
- **Description**: Hello World application using Java 21 features (records, text blocks, pattern matching)

### 2. repo1-java11
- **Repository**: `bisban143/Repo1_for_blitzy_submod_test`
- **Branch**: `java11-compatible`
- **Description**: Hello World application compatible with Java 11

### 3. repo1-weather
- **Repository**: `bisban143/Repo1_for_blitzy_submod_test`
- **Branch**: `feature/weather`
- **Description**: Hello World application with weather display feature using Java 21 and wttr.in API

### 4. repo2-python
- **Repository**: `bisban143/Repo2_for_blitzy_submod_test`
- **Branch**: `main`
- **Description**: Hello World application using Python 3.10+ features (dataclasses, match statements)

## Cross-Submodule Feature: Runtime Context Output

All three submodules have been extended with a parity feature: when each application is run, it additionally prints the host's current **location** (hostname, working directory, timezone), the current **date** (`YYYY-MM-DD`), and the current **time** (`HH:MM:SS`) to standard output, alongside the existing multilingual greeting banner.

The new output lines use identical prefixes across all three implementations so that captured screenshots can be visually compared across submodules:

- `Host: <hostname>`
- `Working directory: <cwd>`
- `Timezone: <zone-id>`
- `Date: YYYY-MM-DD`
- `Time: HH:MM:SS`

These lines are inserted between the existing greeting banner and the existing `Running on: <runtime version>` line, preserving full backward compatibility with the original program output.

### Testing

Each submodule now ships with automated unit tests organized under a literal `test/` directory at the submodule root (overriding Maven's default `src/test/` convention for the Java submodules):

- `repo1-java21/test/java/` — JUnit 5 tests
- `repo1-java11/test/java/` — JUnit 5 tests
- `repo2-python/test/` — pytest tests

### Test Evidence

CI workflow runs capture the standard-output of each program and of each test execution, then persist the captures as evidence files in each submodule's `test/screenshot/` directory:

- `<submodule>/test/screenshot/run-output.txt` — captured stdout from running the application
- `<submodule>/test/screenshot/test-output.txt` — captured stdout from the test suite

Evidence files are also published as downloadable workflow artifacts via `actions/upload-artifact@v4` and committed back to the branch on each green CI run.

## Cloning this Repository

To clone this repository with all submodules:

```bash
git clone --recurse-submodules https://github.com/bisban143/[PARENT_REPO_NAME].git
```

Or if you've already cloned it:

```bash
git submodule update --init --recursive
```

## Structure

```
parent-repo/
├── repo1-java21/       → Repo1 (main branch)
│   ├── src/
│   ├── test/
│   │   ├── java/
│   │   └── screenshot/
│   └── ...
├── repo1-java11/       → Repo1 (java11-compatible branch)
│   ├── src/
│   ├── test/
│   │   ├── java/
│   │   └── screenshot/
│   └── ...
├── repo1-weather/      → Repo1 (feature/weather branch)
└── repo2-python/       → Repo2 (main branch)
    ├── hello_world.py
    └── test/
        ├── test_hello_world.py
        └── screenshot/
```
