# Sprint 1 Task 5: Systemd Services & Logging

## 1. Overview
In modern Linux environments, **systemd** acts as the core initialization system and service manager, while **journald** handles centralized logging. This task focused on ensuring high availability for critical security services and establishing a baseline for system observability. By configuring services to start automatically on boot and querying system logs, we ensure the server remains accessible and auditable without manual intervention.

## 2. Service Management (`systemctl`)
To guarantee continuous protection and remote administration, the following services were persistently enabled:
- **`ssh.service` (OpenSSH Daemon):** Enabled to ensure remote administration access is instantly available following any system reboot or crash.
- **`fail2ban.service` (Intrusion Prevention):** Enabled to guarantee that the automated defense mechanisms against brute-force attacks are strictly active from the moment the OS boots.

*Note: Enabling a service via systemd creates the necessary symlinks to start the service at boot, which is functionally different from simply starting it for the current session.*

## 3. Log Monitoring & Observability (`journalctl`)
Effective troubleshooting and security auditing rely on accurate log analysis. `journalctl` was used to interact with systemd's structured journal:
- **Service-Specific Logs:** Queried recent events for SSH and Fail2Ban to verify proper execution and monitor authentication attempts (`-u` flag).
- **Real-Time Tailing:** Utilized live log tracking (`-f` flag) to observe system behavior, service restarts, and connection drops as they happen.
- **Error Filtering:** Filtered the global journal for system errors (`-p err`) to proactively identify kernel, hardware, or service-level faults.

## 4. Commands Used
```bash
# List all currently active and running services
systemctl list-units --type=service --state=running

# Persistently enable critical services at system boot
sudo systemctl enable ssh
sudo systemctl enable fail2ban

# Query the last 20 log entries for specific background services
sudo journalctl -u ssh -n 20
sudo journalctl -u fail2ban -n 20

# Follow system logs in real-time (live tail)
sudo journalctl -f

# Filter global system logs to show only Error level messages or higher
sudo journalctl -p err
