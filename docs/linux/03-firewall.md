# Sprint 1 Task 3: UFW Firewall

## Logic Applied (Default Deny)
Following the principle of least privilege, the firewall is configured to drop all incoming connections by default, while allowing all outgoing traffic for updates and external communications. Only explicitly required ports are opened.

## Applied Rules
- **22/tcp (SSH):** Allowed to maintain remote administration access.
- **80/tcp (HTTP):** Allowed for future reverse proxy/web server configuration (Sprint 3).
- **443/tcp (HTTPS):** Allowed for future secure web traffic (Sprint 3).

## Commands Used
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status verbose
