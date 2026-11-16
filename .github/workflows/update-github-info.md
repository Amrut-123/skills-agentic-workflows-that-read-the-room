---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  github:
    toolsets:
      - repos
  web-fetch: {}
  edit: {}

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request: {}

engine:
  id: copilot
  copilot-sdk: true
---

Read `notes/mona-notes.md` using GitHub repository API tools, not terminal, CLI, or sandboxed commands.

Web-fetch:
- https://github.blog/latest/
- https://github.blog/changelog/

Use those sources and Mona's notes to update `site/content/github-info.md`.

Open a pull request for Mona to review the proposed changes.

Do not write directly to `main`.