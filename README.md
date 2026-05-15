# Parent Repository with Submodules

This repository demonstrates Git submodules by linking to multiple branches across different repositories.

## Submodules

This repository contains 3 submodules:

### 1. repo1-java21
- **Repository**: `bisban143/Repo1_for_blitzy_submod_test`
- **Branch**: `main`
- **Description**: Hello World application using Java 21 features (records, text blocks, pattern matching)

### 2. repo1-java11
- **Repository**: `bisban143/Repo1_for_blitzy_submod_test`
- **Branch**: `java11-compatible`
- **Description**: Hello World application compatible with Java 11

### 3. repo2-python
- **Repository**: `bisban143/Repo2_for_blitzy_submod_test`
- **Branch**: `main`
- **Description**: Hello World application using Python 3.10+ features (dataclasses, match statements)

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
├── repo1-java11/       → Repo1 (java11-compatible branch)
└── repo2-python/       → Repo2 (main branch)
```
