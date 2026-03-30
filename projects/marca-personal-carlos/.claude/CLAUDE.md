# CLAUDE.md

## Project mode
This project should be edited in small batches to reduce context growth and token waste.

## Default behavior
- Prefer targeted patches over full-file rewrites.
- Never regenerate the entire HTML file unless explicitly asked.
- Read only the relevant ranges before editing.
- Use the project skills when relevant:
  - /small-batch-edit
  - /portfolio-sync
  - /qa-publish-pass

## Versioning rule
When making a major checkpoint:
- duplicate the current version first
- create the next version file
- patch the new version only

Example:
index-v2.html -> index-v3.html

## Output rule
Keep final responses short:
- Changes applied
- Files edited
- Assets used
- Path to open

## Workflow rule
For big requests, split work into phases:
1. structure / functionality
2. copy / content
3. visual polish
4. QA / publish pass
