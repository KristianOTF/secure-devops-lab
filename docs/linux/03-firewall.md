# Sprint 1 Task 3: UFW Firewall

## 1. Overview
Configured the Uncomplicated Firewall (UFW) to secure network traffic and establish a robust baseline defense. By systematically filtering traffic at the network layer, we prevent external entities from probing or exploiting internal services.

## 2. Firewall Logic & Policies
The firewall relies on a strict filtering logic prioritizing security while allowing necessary administrative and web traffic:
- **Default Deny (Incoming)**: Drops all inbound connections by default, ensuring that no port is exposed unless explicitly declared.
- **Default Allow (Outgoing)**: Allows the server to initiate outbound traffic, which is essential for downloading package updates and reaching external APIs.

### Allowed Ports
- **22/tcp (SSH)**: Kept open to maintain secure remote administration access. *(Critical: allowed before enabling UFW to prevent session lockout).*
- **80/tcp (HTTP)**: Opened in preparation for the future reverse proxy and web server configuration (Sprint 3).
- **443/tcp (HTTPS)**: Opened to handle future encrypted web traffic and SSL termination (Sprint 3).

## 3. Commands Used
```bash
# Set baseline security policies
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Allow explicitly required ports
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Activate the firewall and verify the active ruleset
sudo ufw enable
sudo ufw status verbose