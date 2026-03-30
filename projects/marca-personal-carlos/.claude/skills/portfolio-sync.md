---
name: portfolio-sync
description: Use this skill when portfolio categories, thumbnails, videos, and JSON mappings must stay aligned without guessing.
---

# Purpose
Keep the portfolio system aligned across:
- content/data/portfolio-items.json
- video files
- thumbnail files
- category filters in the UI

# Required workflow
1. Read content/data/portfolio-items.json.
2. Read the existing portfolio section code only.
3. Validate every item for:
   - id
   - title
   - category
   - featured or showInAll
   - video path
   - thumbnail path
4. Check that every referenced file exists.
5. If a path is wrong, fix the JSON or the markup with the smallest possible change.
6. Ensure category labels in the UI match the JSON categories exactly.
7. Ensure “Todos” only shows featured items.
8. Ensure specific tabs show all items in that category.
9. Return a compact mismatch report.

# Category map for this project
- fitness-cinematic
- fitness-marca-personal
- marcas-ropa
- otros
- ia-transitions (separate section, not part of the main portfolio tabs)

# Guardrails
- Do not rename assets unless the user explicitly asks.
- Do not invent new categories.
- Do not mix IA transitions into the main service portfolio.
