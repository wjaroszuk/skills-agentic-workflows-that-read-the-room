---
name: update-github-info
description: Keep the GitHub Info page current with practical updates from the GitHub Blog and Changelog.
intent: Help developers learn GitHub faster by keeping the GitHub Info page current with practical, source-backed updates.
on:
  schedule: daily
  workflow_dispatch:
engine:
  id: copilot
  copilot-sdk: true
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
tools:
  edit: 
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
---

# Update GitHub Info

Read `notes/mona-notes.md` first and follow its editorial guidance. Review
`site/content/github-info.md` before making changes.

Use the web-fetch tool to read all three:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Select only recent, accurate updates that are useful to developers learning
GitHub. Keep summaries short and practical, preserve the page's existing
structure and themes, avoid duplicates, and cite the original GitHub Blog,
Changelog, or Awesome Copilot workflows source for every new or revised item.
Do not infer details that the sources do not support.

Edit only `site/content/github-info.md`. If neither source has a relevant
update, or the page already covers the relevant updates accurately, make no
changes and call `noop` with a brief reason.

When you make a meaningful change, open a pull request containing only that
file, request review from Mona (`mona`), and summarize the update and its
official sources in the pull request description. Do not merge the pull request.
