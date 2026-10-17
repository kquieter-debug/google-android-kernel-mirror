# Android Kernel Mirror

> An automated GitHub mirror of [Google Android Common Kernel (ACK)](https://android.googlesource.com/kernel/common).

[![Sync Android Common Kernel](https://github.com/kquieter-debug/google-android-kernel-mirror/actions/workflows/sync-kernel.yml/badge.svg)](https://github.com/kquieter-debug/google-android-kernel-mirror/actions/workflows/sync-kernel.yml)
![Last Sync](https://img.shields.io/github/last-commit/kquieter-debug/google-android-kernel-mirror/main?label=last%20sync)
![License](https://img.shields.io/badge/license-GPL--2.0-blue)

---

## Purpose

The sole purpose of this repository is to **MIRROR** the Google Android Common Kernel (ACK) from
[android.googlesource.com/kernel/common](https://android.googlesource.com/kernel/common).

Specifically, this mirror tracks:

- The **MAINLINE** branch of ACK
- **All lts branches that have not yet reached End-of-Life**

No modifications, patches, or downstream changes are applied. This is a read-only, best-effort mirror.

> All source code is the property of Google LLC and the Linux Kernel community, licensed under **GPL-2.0**.
> This repository only exists to provide convenient, automated access to the upstream source.

---

## IMPORTANT: Source-Only Snapshot

This mirror provides **source code snapshots only** — it does **NOT** contain upstream commit history due to the limited push of github.

- ✅ Full working tree of the tracked branch at the time of sync
- ❌ No upstream commit history (`git log` will only show a single sync commit)
- ❌ No upstream commit messages, authors, or timestamps
- ❌ No upstream tags

Each sync produces a **single squashed commit** representing the latest source state.
If you need the full history, clone the [upstream ACK repo](https://android.googlesource.com/kernel/common) directly.

---

## Branches

Branches are synced automatically every week. Only **NON-EOL-LTS** and **MAINLINE** branches are tracked.

| Branch | Kernel Version | Status |
|--------|----------------|--------|
| `main` | mainline | ✅ Active |
| `android17-6.18-lts` | 6.18 | ✅ Active |
| `android16-6.12-lts` | 6.12 | ✅ Active |
| `android15-6.6-lts` | 6.6 | ✅ Active |
| `android14-6.1-lts` | 6.1 | ✅ Active |
| `android13-5.15-lts` | 5.15 | ✅ Active |
| `android13-5.10-lts` | 5.10 | ✅ Active |
| `android12-5.10-lts` | 5.10 | ✅ Active |
| `android12-5.4-lts` | 5.4 | ❌ EOL |

> The exact set of branches may change over time as upstream branches reach EOL
> or new ones are created. The workflow configuration is the source of truth.

---

## How Synchronization Works

Syncing is handled by [GitHub Actions](.github/workflows/sync-kernel.yml).

Each sync creates an **orphan branch containing a single commit** that holds the
latest source tree. Upstream commit history is intentionally **not** preserved.

Strategy:
  1. Shallow clone upstream (--depth=1) → source only
  2. Orphan branch (single commit) → no history
  3. pack.packSizeLimit=1g → bypass 2GB limit
  4. Auto-retry + reduced pack size → network fault
  5. Incremental batched push → last-resort path

---

## Use as a source tree ( NOT as a history source )
### Since there is no commit history, use this mirror to:

- Read / build the source at a given point in time
- Diff against your own tree
- Vendor into your project
- Do not expect to git blame, git bisect, or git cherry-pick upstream commits from this mirror.

---
