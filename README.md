# FilePilot — Python File Automation

[![Python Tests](https://github.com/erkankoyun/FilePilot-Python-Automation/actions/workflows/tests.yml/badge.svg)](https://github.com/erkankoyun/FilePilot-Python-Automation/actions/workflows/tests.yml)

A small, production-minded Python automation project that organizes files from a download/inbox folder into configurable categories while protecting existing files from accidental overwrite.

## Highlights

- Organizes files by extension
- Configurable category rules using JSON
- Safe duplicate naming instead of overwriting existing files
- `--dry-run` mode to preview changes before moving files
- Structured JSON Lines activity log
- Cross-platform paths with `pathlib`
- Dependency-free Python implementation
- Automated unit tests with temporary directories
- GitHub Actions CI across supported Python versions

## Example

Input:

```text
Downloads/
  invoice.pdf
  photo.jpg
  project.zip
  notes.txt
  unknown.bin
```

Output:

```text
Downloads/
  Documents/
    invoice.pdf
    notes.txt
  Images/
    photo.jpg
  Archives/
    project.zip
  Other/
    unknown.bin
```

## Requirements

Python 3.11+

No third-party packages are required.

## Usage

Preview changes first:

```bash
python organizer.py --source ~/Downloads --dry-run
```

Organize the directory:

```bash
python organizer.py --source ~/Downloads
```

Use a custom configuration:

```bash
python organizer.py --source ~/Downloads --config config.example.json
```

Use a custom log location:

```bash
python organizer.py --source ~/Downloads --log ~/filepilot.log.jsonl
```

## Configuration

`config.example.json` maps destination folder names to file extensions. Extensions are case-insensitive and may be written with or without the leading dot.

## Safety behavior

FilePilot never intentionally overwrites an existing destination file. If `report.pdf` already exists, the next file is moved as `report (1).pdf`, then `report (2).pdf`, and so on.

Use `--dry-run` before organizing an important folder.

## Tests

Run locally:

```bash
python -m unittest discover -s tests -v
```

## Project structure

```text
.
├── organizer.py
├── config.example.json
├── tests/
│   └── test_organizer.py
├── .github/
│   └── workflows/
│       └── tests.yml
├── .gitignore
├── LICENSE
└── README.md
```

## Skills demonstrated

Python, CLI design, filesystem automation, JSON configuration, safe file operations, structured logging, unit testing, GitHub Actions, and cross-platform scripting.

## Author

**Erkan Koyun**  
Software Developer | PHP • Laravel • Python | Backend Development | IT Specialist
