---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions: read-all
engine: copilot
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    base-branch: main
    max: 1
---

# Update GitHub Info

Maintain the GitHub Info website content for Mona.

1. Read `notes/mona-notes.md` and the current `site/content/github-info.md`.
2. Use the GitHub repository API tools to read repository guidance or reference files. Do not use terminal, CLI, or sandboxed commands for repository guidance or reference files.
3. Use the web-fetch tool to read https://github.blog/latest/ and https://github.blog/changelog/.
4. Identify practical, relevant GitHub updates that fit Mona's editorial angle. Keep summaries short, cite the source for each update, and avoid duplicating information already present.
5. Use the edit tool to update `site/content/github-info.md` with the resulting content. Keep unrelated content unchanged.
6. Use the `create-pull-request` safe output to open a pull request targeting `main` for Mona to review. Include a concise title and body describing the sources consulted and the content changes.

Only propose changes through the pull request. Do not write directly to `main`.