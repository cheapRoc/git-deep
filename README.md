# git-deep

Traverse down nested directories and pull/fetch all found git repos.

For simple tasks like updating a slew of projects or performing scripting work
across multiple git repos within the current directory.

## Usage

```
-v, --version           List version information
-h, --help              List commands and information
-l, --list              Find and list all git directories
-d, --dry-run           Don't perform any actions on found git repos
-u, --update            Iterate over every nested repo and fetch/update each
```

## Examples

- `git deep -u` - Update all nested git projects
- `git deep -l` - List all nested git projects, scriptable for solving for things like...

_Who is banned from vacation during the next alpha release?_

```
for microsvc in $(git deep -l); do git --git-dir=$microsvc/.git log --pretty="%ae" remotes/origin/beta..remotes/origin/master 2>/dev/null; done | sort | uniq -c | sort -r
```
