# Contributing to Incendium 121 Datapack

Thank you for your interest in contributing to the incendium121-datapack project at NAF Studio. This document outlines our engineering standards, contribution workflow, and datapack structure conventions.

---

## 1. Branching Strategy & Workflow

This project adheres to a streamlined Trunk-based Development model:

- `main`: The stable production branch. All modifications targeting `main` must be submitted via a Pull Request (PR) and pass all continuous integration checks.
- Working branches should be branched directly from `main` using structured naming:
  - `feat/<short-description>`: New dimension attributes, pack format support, or features.
  - `fix/<short-description>`: Bug fixes, coordinate calculation issues, or JSON syntax corrections.
  - `chore/<short-description>`: CI workflow updates, release actions, or repository tooling.
  - `docs/<short-description>`: Documentation updates and installation guide revisions.

---

## 2. Commit Standards: Conventional & Atomic Commits

### 2.1. Conventional Commits

All commit messages must adhere to the Conventional Commits specification:

```text
<type>(<scope>): <short description in lowercase>
```

- Allowed Types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`.
- Optional Scope: Component or dimension affected (e.g., `nether`, `format`, `release`).
- Description: Concise imperative sentence in lowercase without trailing punctuation.

### 2.2. Atomic Commits

- Each commit must address a single logical concern.
- Never mix documentation revisions, JSON schema updates, and workflow modifications in the same commit.
- Every commit must leave the datapack in a valid, loadable state.

---

## 3. Code Style & Datapack Standards

### 3.1. JSON Formatting & Schema

- Indentation: 2 spaces.
- Validation: Ensure all JSON files pass standard parser validation prior to committing:

  ```bash
  python -m json.tool pack.mcmeta
  ```

- Compatibility: Always verify dimension type attributes conform to vanilla Minecraft data definitions for target versions.

### 3.2. Verification in Minecraft

Before submitting changes, test the datapack in a local singleplayer or test server environment:

- Verify loading status via `/datapack list`.
- Verify reload execution via `/reload`.
- Travel through a Nether portal and verify 1 block in the Nether equals 1 block in the Overworld.

---

## 4. Pull Request Process

1. Ensure your feature branch is rebased on top of the latest `main`.
2. Verify all JSON files are syntactically valid.
3. Open a Pull Request on GitHub. The pre-configured template will be populated automatically.
4. Provide a clear summary of your changes and reference relevant issues (e.g., `Closes #12`).
5. Merging requires passing CI workflows and maintainer approval.
