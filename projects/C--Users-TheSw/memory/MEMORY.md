# Memory

## User Preferences
- **Memory sync (session start)**: At the START of every new conversation, run `bash ~/.claude/sync-memory.sh` to push+pull memory with GitHub. This pushes local changes first, then pulls any mobile changes. Do this before anything else.
- **Memory sync (session end)**: Also run `bash ~/.claude/sync-memory.sh` after any session where memory files were changed.
- GitHub repo: `arthur-vandelay/claude-memory` (public). Files with "private" in the name are excluded from sync. On mobile Claude Code, user pastes: `clone arthur-vandelay/claude-memory`
- When user asks for a "plain text list" of emails, they need a copy-pasteable list at the bottom (e.g. comma-separated or one per line) for pasting into email fields, in addition to the descriptive per-student breakdown above it.
- **VeraFast roadmap workflow**: After completing each checklist item, STOP and check in with the user before starting the next item. Do not auto-advance to the next task.
- **VeraFast contact email**: All VeraFast/Veracross projects should use `verafast@fleisch.family` as the contact/support email (not `a@fleisch.family`). This applies to email copy-to-clipboard, mailto links, license prompts, website, etc.
- **"mem" shorthand**: When user says `mem <something>`, add that item to the "Things to Remember" section below. When user says just `mem`, display the current list. When user says `mem private <something>`, add it to `MEMORY-private.md` instead (never synced to GitHub/public).

## Things to Remember
- Avi Sher owes me Book 6 of Dungeon Crawler Carl
- Sam Arbesman has Book 7 of Dungeon Crawler Carl
- Jackie McCrea's daughter's name is Riley
- Talia can't do lilies — never get her lilies when buying flowers

## Veracross MCP Server
- Located at `~/.veracross/server.py` with client at `~/.veracross/veracross_client.py`
- Configured as stdio MCP server in `~/.claude.json`
- The Veracross API returns students and parents as separate endpoints; parent emails are NOT fields on the student endpoint
- `query_students` was enhanced with `include_parents=true` to cross-reference the parents endpoint and inject `parent_1_name`, `parent_1_email`, `parent_2_name`, `parent_2_email` into student records
- Some parents have different last names than their children (married names, hyphenated names, etc.)
- School: Fuchs Mizrachi School
- API write scopes use `{endpoint}:update` convention (e.g. `courses:update`)
- There is NO `students:update` or `parents:update` scope — student/parent demographic fields are NOT updatable via API
- `contact_info` endpoint (scope: `contact_info:update`) covers emails & phones for ANY person (students, parents, staff). Person ID = student/parent ID
- Contact info fields: email_1, email_2, home_phone, mobile_phone, business_phone
- Tools: `update_contact_info(person_id, updates)` and `query_contact_info(name)`
- `test_write_scopes.py` can be re-run to check which write scopes are available

## VeraFast App
- Desktop app for exploring Veracross school data (Python/Tkinter, PyInstaller for EXE)
- Single consolidated source: `veracross_explorer.py` with `EDITION` flag ("personal" / "shared")
- See [verafast_roadmap.md](verafast_roadmap.md) for full roadmap and task tracking

## Cloudflare
- Wrangler CLI authenticated (OAuth, akivaf@gmail.com)
- Account ID: `8b7a3732221db1f06716a3aa79a25cc1`
- Has access to: Workers, KV, Pages, D1, zones (read), etc.
- Website: fleisch.family (hosted on Cloudflare Pages)
- Use `wrangler` commands to manage Workers, KV, Pages deployments

## AVI Conversion Project ("avi project")
- Base path: `C:\Fleischtography Dropbox\Akiva Fleischmann\Akiva's Pictures and Video`
- Workflow: User specifies which year folders to process
  1. Find all `.avi` files in the specified folders
  2. Convert each AVI to MP4 using ffmpeg
  3. Send original AVI files to the trash (not permanent delete)
  4. Review each video file and rename: keep original filename, append a space + AI-generated description of the video content
- Tool: ffmpeg for conversion

## File Locations
- Screenshots: `C:\Fleischtography Dropbox\Akiva Fleischmann\Screenshots\`

## Key Details
- User: Akiva Fleischmann (afleischmann@fuchsmizrachi.org)
- See [veracross.md](veracross.md) for Veracross-specific notes
