
# AI-Assisted Development Utilities

This repository contains a collection of scripts and prompts designed to aid in software development tasks, particularly those involving interaction with AI code analysis tools.

## Tools

### `gathercode`

A Python script (`gathercode`) that traverses a project directory, collects source code files based on specified extensions, filters out excluded directories/files (respecting `.gitignore`), and concatenates the content into a single formatted output. This output is suitable for pasting into Large Language Models (LLMs) for analysis, review, or refactoring tasks.

**Key Features:**

*   Collects code based on file extensions.
*   Excludes common temporary/build directories and files.
*   Optionally respects `.gitignore` rules.
*   Allows specifying additional exclusions.
*   Can limit the total size of the gathered code.
*   Formats output with clear file boundaries (`--- START FILE: ... ---`, `--- END FILE: ... ---`).

**Usage:**

```bash
./gathercode <project_root> [options]
```

Run `./gathercode --help` for detailed options.

### `smthfy`

A bash script (`smthfy`) designed to perform a global search-and-replace operation within a project directory. It appears tailored for renaming components (e.g., ROM names based on arguments like `$oldromname`, `$newromname`). It also renames specific `.mk` and `.dependencies` files based on the provided names.

**Caution:** This script directly modifies files in place and automatically stages all changes in git (`git add .`). Use with care.

**Usage:**

```bash
./smthfy <old_string> <new_string>
```

### `mergesub`

A bash script (`mergesub`) that uses `git subtree` to add the history of a specific directory (`$1`) from another repository/branch (`$2`) into the current repository.

**Usage:**

```bash
./mergesub <prefix_directory> <remote_and_branch>
# Example: ./mergesub features/newfeature upstream/main
```

## AI Prompts (`sysprompts/` & `promptRecomendations.md`)

*   **`sysprompts/`**: This directory contains system prompts designed to configure an AI assistant (like ChatGPT, Claude, etc.) for specific code analysis tasks.
    *   `codeAnalysis.md`: General code analysis.
    *   `androidAnalysis.md`: Android code analysis (Kotlin, Jetpack, Hilt).
    *   `androidAnalysisKoin.md`: Android code analysis (Kotlin, Jetpack, Koin).
    *   `KMPhelper.md`: (Currently empty) Intended for Kotlin Multiplatform analysis.
*   **`promptRecomendations.md`**: Provides guidance and examples on how to write effective user prompts when interacting with the AI assistant configured using the system prompts above, particularly for Android code review.

These prompts help ensure the AI focuses on relevant aspects like best practices, potential bugs, performance, and maintainability according to modern development standards.
