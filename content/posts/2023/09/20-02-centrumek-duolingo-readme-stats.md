---
title: Duolingo.com Stats
date: 2023-09-20 02:54:20 +00:00
tags:
  - centrumek
  - GitHub Actions
draft: false
repo: centrumek/duolingo-readme-stats
marketplace: https://github.com/marketplace/actions/duolingo-com-stats
version: v1.0.0
dependentsNumber: 1
---


Version updated for **centrumek/duolingo-readme-stats** to version **v1.0.0**.
- This publisher is shown as erified by GitHub.
- This action is used across all versions by **1** repositories.

Go to the [GitHub Marketplace](https://github.com/marketplace/actions/duolingo-com-stats) to find the latest changes.

## Release notes

# First Release!

Automatically add and keep up to date your latest stats from [duolingo.com](https://www.duolingo.com/).

|   Username   | Day Streak | Total XP |
|:------------:|:----------:|:--------:|
| 👤 Centrumek |   🔥 257   | ⚡ 23871  |

|    Language    | Level |   XP    |
|:--------------:|:-----:|:-------:|
| 🇺🇦 Ukrainian | 👑 36 | ⚡ 8965  |
| 🇯🇵 Japanese  | 👑 9  | ⚡ 4780  |
|  🇪🇸 Spanish  | 👑 76 | ⚡ 10126 |

## Usage

Add these two placeholders somewhere in your `README.md`, they will get replaced by the action.

```html
<!--START_SECTION:duolingoStats-->

<!--END_SECTION:duolingoStats-->
```

Create a GitHub Action in your repository, you can call it `duolingo-readme-stats.yml`.

```yaml
name: Duolingo README Stats Action

on:
  schedule:
    - cron: '0 0 * * *' # Runs at 00:00 UTC every day
  workflow_dispatch:

jobs:
  update-readme:
    name: Update readme with your duolingo stats
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v3
      - uses: centrumek/duolingo-readme-stats@main
        with:
          DUOLINGO_USER_ID: <Your duolingo.com user ID>
```

`DUOLINGO_USER_ID` variable can be found in browser DevTools [Fn + F12]

- `Application` > `Local Storage` > `https://www.duolingo.com/` >
  e.g. `duo.appLogo` > `{"730772122":{"canShowLogoDot":true}}`.
- `Network` > `Fetch/XHR` > e.g. `https://zombie.duolingo.com/22/web.json?user=730772122`.

## Configuration

There are a few configuration options you can use in your GitHub Action.

|    Parameter     |                   Description                    |                        Default                        | Required |
|:----------------:|:------------------------------------------------:|:-----------------------------------------------------:|:--------:|
| DUOLINGO_USER_ID |            Your duolingo.com user ID             |                       730772122                       | **Yes**  |
|   COMMIT_EMAIL   |     Email used while committing to the repo      | 41898282+github-actions[bot]@users.noreply.github.com |    No    |
|    COMMIT_MSG    | Commit message used while committing to the repo |      💬 Updated README with your duolingo stats       |    No    |
| COMMIT_USERNAME  |    Username used while committing to the repo    |                  duolingo-stats-bot                   |    No    |
|    FILE_NAME     |       Define a specific file in your repo        |                       README.md                       |    No    |
|  SHOW_LANGUAGES  |            Toggle the languages table            |                         true                          |    No    |
