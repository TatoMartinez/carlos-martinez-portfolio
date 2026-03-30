---
name: small-batch-edit
description: Use this skill when making targeted edits to an existing page without rewriting the whole file. Best for 1-3 concrete changes in a single pass.
---

# Purpose
Apply small, direct edits to an existing page while minimizing context usage and avoiding full-file rewrites.

# When to use
Use this skill when the user asks for things like:
- change one image
- adjust overlay opacity
- update one section's copy
- tweak one component
- add one interaction
- create a new version file from an existing one

Do not use this skill for a complete redesign.

# Required workflow
1. Read only the file ranges that matter.
2. Identify the exact selectors, sections, IDs, classes, or content blocks involved.
3. Edit only the minimum necessary code.
4. Prefer patch-style updates over rewriting the entire file.
5. If creating a new version, duplicate the source file first, then patch the new file.
6. Verify all referenced asset paths exist before finalizing.
7. Return a short completion report.

# Output format
- Changes applied
- Files edited
- Assets referenced
- Manual checks recommended

# Guardrails
- Never rewrite the whole HTML file unless explicitly required.
- Never dump a full file into chat.
- Keep edits localized.
- Preserve the current visual identity unless instructed otherwise.
