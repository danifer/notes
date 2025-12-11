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

1. **Format**: Single sentence at the top of the file, followed by a blank line
2. **Content**: Include relevant keywords that would be used in grep searches
3. **Purpose**: Enable quick identification of file contents via grep/search

### Summary Examples

**Good summaries** (keyword-rich):
```markdown
PostgreSQL database commands for createdb, psql, pg_dump, pg_restore, export to CSV/JSON, remote access, and database size queries.

[Rest of file content...]
```

```markdown
FFmpeg commands for video and audio processing including reduce size, extract audio, remove silence, and concatenate files.

[Rest of file content...]
```

**Bad summaries** (not keyword-rich):
```markdown
This file contains PostgreSQL information.

[Rest of file content...]
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

## Maintenance Tasks

### Reorganizing All Files

To reorganize all files in this directory:

1. Convert any `.txt` files to `.md`
2. Standardize all filenames to `snake_case`
3. Verify all files (except README.md and CLAUDE.md) have keyword-rich summaries
4. Ensure each summary is followed by a blank line

### Adding New Files

When adding new note files:

1. Use `.md` extension
2. Use `snake_case` naming
3. Add a keyword-rich summary as the first line
4. Follow with a blank line before content

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
