# Container Escape Check For sh (容器逃逸检测 sh 兼容版)

[![GitHub stars](https://img.shields.io/github/stars/gkdgkd123/container-escape-check-sh)](https://github.com/gkdgkd123/container-escape-check-sh)
[![GitHub issues](https://img.shields.io/github/issues/gkdgkd123/container-escape-check-sh)](https://github.com/gkdgkd123/container-escape-check-sh/issues)
[![GitHub forks](https://img.shields.io/github/forks/gkdgkd123/container-escape-check-sh)](https://github.com/gkdgkd123/container-escape-check-sh)
[![Forked From](https://img.shields.io/badge/Forked%20from-TeamsSix-blue)](https://github.com/teamssix/container-escape-check)
[![Maintainer](https://img.shields.io/badge/Maintainer-gkdgkd123-green)](https://github.com/gkdgkd123)

![container-escape-check](https://socialify.git.ci/gkdgkd123/container-escape-check-sh/image?description=1&font=Inter&forks=1&issues=1&language=1&logo=https%3A%2F%2Favatars.githubusercontent.com%2Fu%2F49087564&owner=1&pattern=Circuit%20Board&pulls=1&stargazers=1&theme=Dark)

[中文](https://github.com/gkdgkd123/container-escape-check-sh/blob/master/README_ZH.md) | EN

# Introduction

**原版仅适配bash环境，此版本可在sh上使用，适配无bash环境，并修复部分bug。**
**This is a POSIX sh compatible fork.**

Original tool requires `bash`, but many minimal container images (like **Alpine Linux**) only have `sh` installed by default. This version has been refactored to support `sh`, making it run smoothly in almost any Linux container environment.

This script is used to detect Docker container escape methods. The following methods are currently supported:

1. Privileged Mode
2. Mount docker Socket
3. Mount host procfs
4. Mount host root or etc directory
5. Open Docker Remote API
6. CVE-2016-5195 DirtyCow
7. CVE-2020-14386 
8. CVE-2022-0847 DirtyPipe
9. CVE-2017-1000112
10. CVE-2021-22555
11. Mount Host Var Log
12. CAP_DAC_READ_SEARCH (Requires container to support capsh command)
13. CAP_SYS_ADMIN (Requires container to support capsh command)
14. CAP_SYS_PTRACE (Requires container to support capsh command)
15. CVE-2022-0492

# ✨ Usage

Run this script with one command in the container (Supports `sh`).

### Method 1: Remote Execution (Recommended)

```bash
# Using wget
wget [https://raw.githubusercontent.com/gkdgkd123/container-escape-check-sh/main/container-escape-check.sh](https://raw.githubusercontent.com/gkdgkd123/container-escape-check-sh/main/container-escape-check.sh) -O- | sh

# Using curl
curl -sL [https://raw.githubusercontent.com/gkdgkd123/container-escape-check-sh/main/container-escape-check.sh](https://raw.githubusercontent.com/gkdgkd123/container-escape-check-sh/main/container-escape-check.sh) | sh

```

### Method 2: Clone and Run

```bash
git clone [https://github.com/gkdgkd123/container-escape-check-sh.git](https://github.com/gkdgkd123/container-escape-check-sh.git)
cd container-escape-check-sh
chmod +x container-escape-check.sh
./container-escape-check.sh

```

If it helps you, please give a star ✨ to both this repo and the [original repo](https://github.com/teamssix/container-escape-check)!

# ⚠️ Notes

* **Compatibility:** This version is specifically optimized for `sh` shell environments.
* This script needs to be run inside the docker container.
* Most of the detection methods here are based on experience, and there may be false positives or omissions. If you find these problems, please submit an Issue.

# Acknowledgements

* Original Author: [TeamsSix](https://github.com/teamssix)
* Original Repo: [container-escape-check](https://github.com/teamssix/container-escape-check)

# Changelog

## sh-v0.3 (Current)  

* Ported entire logic from Bash to POSIX Sh.
* Fixed syntax errors when running in Alpine/Minimal environments.

## Original History

* **v0.3 2022.4.7**: Add CVE-2022-0492, Enhanced privileged mode & /var/log detection.
* **v0.2 2022.3.30**: Add CVE-2017-1000112, CVE-2021-22555, CAP checks, etc.
* **v0.1 2022.3.18**: Initial release.

