---
name: update-github-info
description: Keep the GitHub Info page current with practical updates from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

engine: copilot

tools:
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    reviewers: [mona]
    draft: false
    max: 1
---

# Update GitHub Info

Keep `site/content/github-info.md` useful, accurate, and current for developers learning GitHub.

## Sources

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Use web fetch to read https://github.blog/latest/.
3. Use web fetch to read https://github.blog/changelog/.
4. Base updates only on relevant, verifiable information from those official sources. Preserve source links for any blog or changelog information you use.

## Update

Review `site/content/github-info.md` and update it with concise, practical guidance that fits its existing themes. Prefer useful changes for developers over a comprehensive news recap. Keep existing accurate material, avoid unsupported claims, and do not make speculative or cosmetic edits. If there is no meaningful update to make, leave the file unchanged and do not open a pull request.

Only edit `site/content/github-info.md`. Review the resulting diff for accuracy, concise wording, and working source URLs. When there are meaningful changes, use the configured pull-request safe output to open one pull request requesting review from Mona. Do not write directly to the default branch or modify any other files.