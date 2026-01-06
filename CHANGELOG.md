# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- `gh collab remove <username>` - Remove a collaborator
- `gh collab list` - List all collaborators with their permission levels
- `gh collab check <username>` - Check if a user is already a collaborator
- `--permission` flag to set access level
- Batch add multiple users
- Config file support
- Interactive mode with fuzzy user search
- Organization teams support

## [1.0.0] - 2026-01-05

### Added
- Initial release
- `gh collab add <username>` command to add collaborators
- `-R` flag to specify target repository
- Auto-detection of current repository from git remote
- Default push (write) permission level
