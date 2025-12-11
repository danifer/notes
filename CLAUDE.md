# Claude Instructions for Notes Organization

This file contains instructions for organizing and maintaining the notes files in this directory.

## File Naming Conventions

All note files should follow these standards:

1. **File Extension**: Use `.md` (Markdown) for all note files
2. **Naming Convention**: Use `snake_case` (underscores) for multi-word filenames
   - Good: `bash_scripting.md`, `git_self_hosted_repo_setup.md`
   - Bad: `bash-scripting.md`, `bashScripting.md`, `bash scripting.md`
3. **Special Files**: `README.md` should remain as-is (standard convention)

### Converting File Extensions

When converting files from `.txt` to `.md`:
```bash
for f in *.txt; do mv "$f" "${f%.txt}.md"; done
```

### Standardizing File Names

When standardizing filenames to snake_case, replace hyphens and other separators with underscores:
```bash
# Example conversions:
postfix-block_by_sender.md → postfix_block_by_sender.md
asdm-for-asa5505.md → asdm_for_asa5505.md
```

## File Content Structure

Every note file must have a **keyword-rich summary** as the first line.

### Summary Requirements

1. **Format**: Single sentence at the top of the file
2. **Separator**: Followed by a blank line, then `---`, then another blank line
3. **Content**: Include relevant keywords that would be used in grep searches
4. **Purpose**: Enable quick identification of file contents via grep/search

### Summary Examples

**Good summary format** (keyword-rich with separator):
```markdown
PostgreSQL database commands for createdb, psql, pg_dump, pg_restore, export to CSV/JSON, remote access, and database size queries.

---

Install Postgres from Homebrew:
    brew update; brew install postgresql
...
```

**Complete example**:
```markdown
Git version control commands for commit, branch, merge, reset, stash, push, pull, diff, and remote repository management.

---

Undo git add before commit:
    git reset FILE

Update the message for a commit
    git commit --amend -m "an updated commit message"
...
```

**Bad summary** (not keyword-rich):
```markdown
This file contains PostgreSQL information.

---

[Content...]
```

### Common Grep Search Terms

When writing summaries, consider including these types of keywords:
- **Technologies**: postgres, mysql, redis, git, symfony, nginx, apache
- **Operations**: create, delete, rename, replace, convert, export, import, backup, restore
- **File types**: csv, json, xlsx, sql, xml, pdf
- **Concepts**: api, database, server, user, permission, authentication, configuration
- **Tools**: psql, grep, find, rsync, ssh, docker

## Adding Summaries to Files

When adding or updating summaries:

1. Read the file content to understand what it contains
2. Identify the main topics, commands, and technologies covered
3. Write a single-sentence summary that includes:
   - Primary technology/tool name
   - Key operations or use cases
   - Important related keywords
4. Place the summary as the first line of the file
5. Add a blank line after the summary

### Example Workflow

```markdown
# Before (no summary)
Install Postgres from Homebrew:
    brew update; brew install postgresql

Create a database
    createdb -e -E 'UTF-8' -O {dbowner} -h{host} -U{user} {database name}
...

# After (with summary)
PostgreSQL database commands for createdb, psql, pg_dump, pg_restore, export to CSV/JSON, remote access, and database size queries.

Install Postgres from Homebrew:
    brew update; brew install postgresql

Create a database
    createdb -e -E 'UTF-8' -O {dbowner} -h{host} -U{user} {database name}
...
```

## Indentation Standards

All files must use consistent indentation for hierarchical content organization.

### Indentation Rules

1. **Unit Size**: Use **4 spaces** as the standard indentation unit (not tabs)
2. **Hierarchical Levels**:
   - Primary level (commands, descriptions): **4 spaces**
   - Secondary level (sub-commands, options): **8 spaces**
   - Tertiary level (nested options, examples): **12 spaces**
   - Continue in 4-space increments for deeper nesting

### Examples

**Correct indentation (4-space increments):**
```markdown
Create a database
    createdb -e -E 'UTF-8' -O {dbowner} -h{host} -U{user} {database name}

Clone a database (must be inactive/no active connections)
    CREATE DATABASE target_db WITH TEMPLATE source_db OWNER your_user;

Add user to group:
    usermod -a -G groupname username
        usermod -a -G sudo username
```

**Incorrect indentation (2-space or inconsistent):**
```markdown
Create a database
  createdb -e -E 'UTF-8' -O {dbowner} -h{host} -U{user} {database name}

Add user to group:
  usermod -a -G groupname username
    usermod -a -G sudo username
```

### Converting Indentation

To convert files from 2-space to 4-space indentation, double all leading spaces:

```python
import re

with open(filename, 'r') as f:
    lines = f.readlines()

converted_lines = []
for i, line in enumerate(lines):
    if i == 0:  # Skip summary line
        converted_lines.append(line)
        continue

    match = re.match(r'^( +)(.+)$', line)
    if match:
        spaces = match.group(1)
        rest = match.group(2)
        new_spaces = ' ' * (len(spaces) * 2)
        converted_lines.append(new_spaces + rest + '\n')
    else:
        converted_lines.append(line)

with open(filename, 'w') as f:
    f.writelines(converted_lines)
```

### Verifying Indentation

Check for files using 2-space indentation:
```bash
# Look for lines with exactly 2 spaces followed by non-space
grep -l "^  [^ ]" *.md | grep -v "README.md\|CLAUDE.md"
```

## Blank Line Standards

Blank lines must be truly empty with no spaces or tabs.

### Rules

1. **Empty Lines**: Blank lines should contain only a newline character (`\n`)
2. **No Whitespace**: Blank lines must NOT contain any spaces, tabs, or other whitespace
3. **Purpose**: Ensures clean file formatting and proper diff/version control

### Example

**Correct (truly empty lines):**
```markdown
Create a database
    createdb -e -E 'UTF-8'

Drop a database
    dropdb {database}
```

**Incorrect (spaces on blank line):**
```markdown
Create a database
    createdb -e -E 'UTF-8'

Drop a database
    dropdb {database}
```
*Note: The line between the two sections contains invisible spaces*

### Cleaning Blank Lines

To remove spaces from blank lines in all files:

```python
import os

def clean_blank_lines(filename):
    with open(filename, 'r') as f:
        lines = f.readlines()

    cleaned_lines = []
    for line in lines:
        # If line contains only whitespace, replace with just newline
        if line != '\n' and line.strip() == '':
            cleaned_lines.append('\n')
        else:
            cleaned_lines.append(line)

    with open(filename, 'w') as f:
        f.writelines(cleaned_lines)

# Clean all markdown files
for filename in os.listdir('.'):
    if filename.endswith('.md'):
        clean_blank_lines(filename)
```

### Verifying Blank Lines

Check for files with whitespace in blank lines:
```python
# Files with whitespace-only blank lines
for filename in os.listdir('.'):
    if not filename.endswith('.md'):
        continue

    with open(filename, 'r') as f:
        for line in f:
            if line != '\n' and line.strip() == '':
                print(f"{filename} has whitespace in blank lines")
                break
```

## Maintenance Tasks

### Reorganizing All Files

To reorganize all files in this directory:

1. Convert any `.txt` files to `.md`
2. Standardize all filenames to `snake_case`
3. Verify all files (except README.md and CLAUDE.md) have keyword-rich summaries
4. Add separator: blank line, `---`, blank line after each summary
5. Standardize indentation to 4-space increments for all files
6. Remove spaces from blank lines (blank lines should be truly empty)

Note: Existing markdown formatting (code blocks, etc.) can remain, but new content should use indentation-based organization.

### Adding New Files

When adding new note files:

1. Use `.md` extension
2. Use `snake_case` naming
3. Add a keyword-rich summary as the first line
4. Add separator: blank line, `---`, blank line
5. Use 4-space indentation increments for hierarchical content
6. Ensure blank lines contain no spaces (truly empty lines only)

Note: Use indentation-based organization. Existing markdown formatting can remain where present.

### Verifying Organization

To check if files are properly organized:

```bash
# List all non-.md files (should be empty except .git, .cf, etc.)
ls *.txt 2>/dev/null

# Check for files with hyphens in names
ls -1 *.md | grep -E '(^|[^_])-([^_]|$)'

# Check files missing summaries (look for files starting with ###, #, or commands)
for f in *.md; do
  if [[ "$f" != "README.md" && "$f" != "CLAUDE.md" ]]; then
    head -1 "$f"
  fi
done

# Check for files using 2-space indentation (should return nothing)
grep -l "^  [^ ]" *.md 2>/dev/null | grep -v "README.md\|CLAUDE.md"

# Check for blank lines containing spaces (should return nothing)
python3 << 'PYEOF'
import os
for f in os.listdir('.'):
    if f.endswith('.md') and f not in ['README.md', 'CLAUDE.md']:
        with open(f) as file:
            for i, line in enumerate(file, 1):
                if line != '\n' and line.strip() == '':
                    print(f"{f}:{i} has whitespace in blank line")
                    break
PYEOF
```

## Search Examples

With properly organized files, users can efficiently search with grep:

```bash
# Find files about CSV operations
grep -i "csv" *.md

# Find files about database operations
grep -i "database\|db\|psql\|mysql" *.md

# Find files about file manipulation
grep -i "rename\|convert\|replace" *.md

# Find API-related files
grep -i "api" *.md

# Find files about specific technologies
grep -i "redis\|postgres\|symfony" *.md
```

## Notes

- This directory contains technical reference notes for quick command lookups
- Files are organized for grep-based searching
- Summaries are intentionally verbose to maximize searchability
- All formatting follows Markdown conventions for better readability
