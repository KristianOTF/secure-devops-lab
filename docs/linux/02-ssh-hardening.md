# Sprint 1 Task 2: SSH Hardening

## Overview 
Securing the SSH service on the Ubuntu VM by disabling password-based authentication, disallowing direct root login, and enforcing Ed25519 public-key based authentication.

## Actions Performed

1. SSH Key Generation (Client Side)
Generated a secure Ed25519 key pair on the local machine and deployed the public key to ~/.ssh/authorized_keys with strict permissions.

2. SSH Daemon Configuration (/etc/ssh/sshd_config)
Updated the configuration file with the following security hardening rules:
- PermitRootLogin no
- PasswordAuthentication no
- PubkeyAuthentication yes

3. Service Restart & Verification
Restarted the SSH service to apply changes:
sudo systemctl restart ssh
 
Verified successful key-based login from the host machine and confirmed that password authentication/root login are correctly blocked.
