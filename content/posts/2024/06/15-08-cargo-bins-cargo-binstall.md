---
title: Install cargo-binstall
date: 2024-06-15 08:45:54 +00:00
tags:
  - cargo-bins
  - GitHub Actions
draft: false
repo: cargo-bins/cargo-binstall
marketplace: https://github.com/marketplace/actions/install-cargo-binstall
version: v1.7.1
dependentsNumber: "10"
---


Version updated for **cargo-bins/cargo-binstall** to version **v1.7.1**.
- This action is used across all versions by **10** repositories.

Go to the [GitHub Marketplace](https://github.com/marketplace/actions/install-cargo-binstall) to find the latest changes.

## Release notes

_Binstall is a tool to fetch and install Rust-based executables as binaries. It aims to be a drop-in replacement for `cargo install` in most cases. Install it today with `cargo install cargo-binstall`, from the binaries below, or if you already have it, upgrade with `cargo binstall cargo-binstall`._

#### In this release:

 - Make sure the token is zeroed out/erased on drop (#1761 #1769)
 - Run  `gh auth token` in parallel to fetching from registey (#1733 #1769)
