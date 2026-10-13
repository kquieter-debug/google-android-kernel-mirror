# Android Kernel Mirror
## Let me TEST it ...

> An automated GitHub mirror of [Google Android Common Kernel (ACK)](https://android.googlesource.com/kernel/common).

[![Sync Android Common Kernel](https://github.com/kquieter-debug/google-android-kernel-mirror/actions/workflows/sync-kernel.yml/badge.svg)](https://github.com/kquieter-debug/google-android-kernel-mirror/actions/workflows/sync-kernel.yml)
![Last Sync](https://img.shields.io/github/last-commit/<OWNER>/<REPO>/main?label=last%20sync)
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

## Usage

### Clone (shallow — recommended)

```bash
# Default branch
git clone --depth=1 https://github.com/kquieter-debug/google-android-kernel-mirror.git

# Specific branch
git clone --depth=1 -b android14-6.1 https://github.com/kquieter-debug/google-android-kernel-mirror.git
