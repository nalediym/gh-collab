# gh-collab

A GitHub CLI extension to manage repository collaborators.

> Because typing `gh api repos/blah/blah/collaborators/whoever -X PUT` every time is annoying.

## Installation

```bash
gh extension install nalediym/gh-collab
```

## Usage

```bash
# Add a collaborator to the current repo (auto-detects from git remote)
gh collab add octocat

# Add a collaborator to a specific repo
gh collab add octocat -R myorg/private-repo

# Add with specific permission level
gh collab add octocat --permission admin

# Batch add multiple users
gh collab add alice bob charlie

# Remove a collaborator
gh collab remove octocat

# List all collaborators
gh collab list

# Check if a user is a collaborator
gh collab check octocat

# Show help
gh collab --help
```

## What it does

When you run `gh collab add <username>`, it:

1. Detects the current repository (or uses the one you specify with `-R`)
2. Sends an invitation to the GitHub user
3. They receive an email and need to accept it

The default permission level is **push** (write access).

## Roadmap / Future Features

These are documented as `TODO` comments in the source code. PRs welcome!

- [x] `gh collab remove <username>` - Remove a collaborator
- [x] `gh collab list` - List all collaborators with their permission levels
- [x] `gh collab check <username>` - Check if a user is already a collaborator
- [x] `--permission` flag to set access level (pull/push/admin/maintain/triage)
- [x] Batch add multiple users: `gh collab add user1 user2 user3`
- [ ] Config file for default settings (`~/.config/gh-collab/config`)
- [ ] Interactive mode with fuzzy user search
- [ ] Support for organization teams

## Permission Levels

GitHub supports these permission levels for collaborators:

| Permission | Description |
|------------|-------------|
| `pull`     | Read-only access |
| `push`     | Read and write access (default) |
| `admin`    | Full admin access |
| `maintain` | Manage repo without admin access |
| `triage`   | Manage issues and PRs without write access |

## For Python Developers

If you're more familiar with Python than bash, the script has extensive comments explaining bash concepts in Python terms. Check out the source code!

The core functionality is essentially:

```python
import subprocess

def add_collaborator(repo: str, username: str, permission: str = "push"):
    subprocess.run([
        "gh", "api", 
        f"repos/{repo}/collaborators/{username}",
        "--method", "PUT",
        "--field", f"permission={permission}",
        "--silent"
    ], check=True)
```

## Contributing

1. Fork this repo
2. Check the `TODO` and `FIXME` comments in `gh-collab` for ideas
3. Make your changes
4. Test locally with `gh extension install .` (from the repo directory)
5. Submit a PR!

## License

MIT

## Author

[@nalediym](https://github.com/nalediym)
