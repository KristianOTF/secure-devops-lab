Sprint 1 Task 3: UFW Firewall

Overview
Configured Uncomplicated Firewall (UFW) to secure network traffic, establishing a baseline defense by blocking unwanted access.

Logic Applied
- Default Deny: Drop all incoming connections by default
- Default Allow: Allow all outgoing traffic

Allowed Ports
- 22/tcp (SSH): To maintain remote administration access
- 80/tcp (HTTP): Prepared for future reverse proxy (Sprint 3)
- 443/tcp (HTTPS): Prepared for future secure web traffic (Sprint 3)

Commands Used
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status verbose

Why This Matters
- Principle of Least Privilege: Only explicitly required ports are opened
- Attack Surface Reduction: Blocks unauthorized access attempts on unused ports
