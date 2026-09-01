---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  edit:
  github:
    toolsets: [repos]
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[mona] "
    fallback-as-issue: false
---

# Update GitHub Info

Keep the GitHub Info page current for Mona's website.

## Instructions

1. Read `notes/mona-notes.md` before making any changes.
2. Use the web-fetch tool to read the public gh-aw guidance at:
  - https://github.com/github/gh-aw/blob/main/.github/aw/github-agentic-workflows.md
3. Use the web-fetch tool to read:
   - https://github.blog/latest/
   - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
4. Use the GitHub repository API tools to read relevant repository guidance or reference files before editing.
5. Review the current content in `site/content/github-info.md`.
6. Update only `site/content/github-info.md` with short, practical updates that help developers learn GitHub faster. Attribute facts and changes to the GitHub Blog or GitHub Changelog whenever those sources support them.
7. Open a pull request containing the proposed update for Mona to review. Do not write directly to the default `main` branch, rely on `safe-outputs` with `create-pull-request`.

Only create a pull request when there are meaningful source-backed changes. Open a pull request for Mona to review. Use a pull request title that mentions Mona or GitHub Info. After requesting the pull request, stop.
