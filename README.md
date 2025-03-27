# DevTools Collection

A set of powerful command-line utilities for code management and repository operations.

## Tools Overview

- **gathercode**: Python script that intelligently collects code files while respecting gitignore rules
- **mergesub**: Bash utility for working with git subtrees
- **smthfy**: Android ROM adaptation helper for device tree renaming

## Installation

```bash
git clone https://github.com/your-username/devtools-collection.git
cd devtools-collection
chmod +x gathercode mergesub smthfy  # Make scripts executable
```

## Usage Examples

### Gather Code
```bash
# Collect code with default settings
./gathercode /path/to/project --output codebase.txt

# Custom file types and size limit
./gathercode . --extensions .py .sh --max-size 2048
```

### Merge Subtree
```bash
./mergesub component-name https://github.com/user/repo
```

### Device Adaptation
```bash
./smthfy old_rom_name new_rom_name
```

## Tools Reference

### gathercode
```
Usage: gathercode project_root [OPTIONS]
Options:
  -o, --output       Save output to file
  -e, --extensions   File extensions to include
  --exclude-dirs     Additional directories to exclude
  --max-size         Size limit in KB (default: no limit)
```

### mergesub
```
Adds a subtree from a remote repository
Usage: ./mergesub <local-prefix> <repository-url>
```

### smthfy
```
Bulk renames ROM components for device adaptation
Usage: ./smthfy <old-rom-name> <new-rom-name>
```

## Contributing

Contributions are welcome! Please follow these steps:
1. Open an issue to discuss proposed changes
2. Fork the repository and create a feature branch
3. Include tests for new functionality
4. Submit a pull request with clear description of changes

## License

[MIT](https://choosealicense.com/licenses/mit/)
