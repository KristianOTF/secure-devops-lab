# Sprint 1 Task 1: User Management

## Overview
Created non-root user for daily operations with sudo privileges.

## Users Created

### devops (Primary user)
- UID: 1001
- GID: 1001
- Shell: /bin/bash
- Groups: devops, sudo
- Purpose: Daily administration and development

### Root
- Disabled for direct SSH login (next task)

## Commands Used

```bash
sudo useradd -m -s /bin/bash -G sudo devops
sudo passwd devops
id devops
groups devops
```

## Why This Matters

- **Principle of Least Privilege:** Don't use root for daily tasks
- **Auditability:** All sudo commands are logged
- **Security:** Root account is isolated and protected

## Next Step
SSH hardening with key-based authentication.
