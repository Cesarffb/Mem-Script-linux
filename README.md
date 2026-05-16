# Memory Services for Linux

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Bash](https://img.shields.io/badge/bash-4.0%2B-green)](https://www.gnu.org/software/bash/)
[![systemd](https://img.shields.io/badge/systemd-required-blue)](https://systemd.io/)

**Memory Services** is an interactive installer that sets up two systemd services to proactively manage your Linux system's memory. It helps prevent slowdowns caused by excessive cache or inefficient swap usage, especially during heavy file operations.

## 🚀 Features

- **Swap Refresh Service** – Periodically restarts swap (`swapoff -a && swapon -a`) when:
  - Free memory is ≥ **20%** (adjustable)
  - **OR** swap usage exceeds **20%** (adjustable)

- **Cache Cleaning Service** – Runs as a daemon and clears the page cache (`drop_caches`) when:
  - Buff/cache memory exceeds **40%** of total RAM (adjustable)

- **Interactive Installer** – Choose to install one service, both, or uninstall.

- **Fully Configurable** – Change thresholds, timer frequency, check intervals, and drop cache levels during installation.

- **Logging** – All actions are logged to syslog. View with `journalctl`.

- **Safe & Lightweight** – Uses only standard Linux commands (`free`, `awk`, `sync`, `swapoff/swapon`).

## 📋 Requirements

- Linux distribution with **systemd** (most modern distros)
- **Root access** (script uses `sudo`)
- **bash** and **coreutils** (always present)

Tested on:
- Ubuntu 20.04+
- Debian 11+
- Arch Linux / CachyOS
- Fedora 34+

## 🔧 Installation

### One‑line installer (recommended)

```bash
sudo curl -L https://raw.githubusercontent.com/yourusername/memory-services/main/memory_services.run -o /tmp/memory_services.run && sudo bash /tmp/memory_services.run
