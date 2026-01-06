# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Config file support (`~/.config/gh-collab/config`)
- Interactive mode with fuzzy user search
- Organization teams support

## [1.1.0] - 2026-01-05

### Added
- `gh collab remove <username>` command to remove collaborators
- `gh collab list` command to list all collaborators with permission levels
- `gh collab check <username>` command to check if a user is a collaborator
- `--permission` / `-p` flag to set access level (pull/push/admin/maintain/triage)
- Batch operations: add/remove/check multiple users at once
- Smart API response handling (distinguishes new invites vs existing collaborators)

### Changed
- Improved error messages with more context
- Better output formatting for batch operations

## [1.0.0] - 2026-01-05

### Added
- Initial release
- `gh collab add <username>` command to add collaborators
- `-R` flag to specify target repository
- Auto-detection of current repository from git remote
- Default push (write) permission level
