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
    toolsets: [repos]
  web-fetch: true
  edit: true
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title: "Update GitHub info"
    body: "Updates GitHub information for Mona to review."
engine:
  id: copilot-sdk
---

Read `notes/mona-notes.md` using GitHub repository API tools, not terminal, CLI, or sandboxed commands. Web-fetch https://github.blog/latest/ and https://github.blog/changelog/. Use those sources and the notes to update `site/content/github-info.md`. Propose the change by opening a pull request for Mona to review. Do not write directly to `main`.
