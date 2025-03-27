# Toolset

A collection of utility scripts for code management, source analysis, and repository operations.

## Tools Overview

### gathercode

A Python utility that intelligently collects and formats source code from a project directory:

- Respects `.gitignore` rules and common exclusion patterns
- Formats output with file boundary markers for AI code analysis
- Supports custom file extensions and exclusions
- Includes size limiting to control output volume

Perfect for preparing codebases for analysis with AI assistants using the included system prompts.

### mergesub

A minimal Bash script for git subtree operations that:

- Fetches from a remote repository
- Adds the fetched content as a subtree at a specified path
- Shows the git log for a specific file after the operation

### smthfy

A specialized Bash utility for Android ROM device adaptation that:

- Performs bulk string replacements across files
- Renames specific ROM-related files
- Preserves git history during the renaming process
- Stages all changes automatically

## System Prompts

The `sysprompts` directory contains specialized prompts designed to work with the output of `gathercode`:

- **codeAnalysis.md**: System prompt for general code analysis across various languages
- **androidAnalysis.md**: System prompt specifically tailored for Android codebase review

## Usage Examples

### Code Gathering

```bash
# Basic usage
./gathercode /path/to/project -o output.txt

# With custom extensions and size limits
./gathercode /path/to/project -e .py .js .ts --max-size 5000 -o code_for_analysis.txt

# Excluding additional directories
./gathercode /path/to/project --exclude-dirs tests fixtures -o output.txt
```

### Subtree Operations

```bash
# Add a repository as a subtree
./mergesub target/directory https://github.com/user/repository
```

### ROM Adaptation

```bash
# Rename ROM components from old name to new name
./smthfy old_device_name new_device_name
```

## Installation

Clone the repository and make the scripts executable:

```bash
git clone https://github.com/username/toolset.git
cd toolset
chmod +x gathercode mergesub smthfy
```

## Tools Reference

### gathercode

```
Usage: gathercode project_root [OPTIONS]

Options:
  -o, --output         Save output to file
  -e, --extensions     File extensions to include
  --exclude-dirs       Additional directories to exclude
  --exclude-files      Additional file patterns to exclude
  --no-gitignore       Ignore .gitignore rules
  --max-size KB        Maximum size limit in KB
```

### mergesub

```
Usage: ./mergesub <local-prefix> <repository-url>
```

### smthfy

```
Usage: ./smthfy <old-rom-name> <new-rom-name>
```

## Workflow Example

1. Gather code from your project:
   ```bash
   ./gathercode /path/to/project -o project_code.txt
   ```

2. Use the output with an AI assistant along with the appropriate system prompt from `sysprompts/`

3. For Android projects, use the Android-specific system prompt for more relevant analysis.
