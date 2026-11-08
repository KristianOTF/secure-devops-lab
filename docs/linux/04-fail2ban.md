Sprint 1 Task 4: Fail2Ban

Overview
Installed and configured Fail2Ban to protect the SSH service by monitoring authentication logs and automatically banning IPs that exhibit malicious behavior, such as brute-force attacks.

Logic Applied (SSH Jail)
- enabled = true: Activates the SSH protection jail
- maxretry: 3: Maximum number of failed login attempts allowed
- findtime: 600: Time window (10 minutes) for the failed attempts
- bantime: 3600: Ban duration (1 hour) for the offending IP address

Blocked Access Logs
To monitor currently banned IPs and failed attempts, the status command is used. 
Running `sudo fail2ban-client status sshd` outputs the "Currently banned" count and the exact "Banned IP list" interacting with the UFW firewall.

Commands Used
sudo apt install -y fail2ban
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local
sudo systemctl restart fail2ban
sudo fail2ban-client status
sudo fail2ban-client status sshd

Why This Matters
- Brute-Force Protection: Automatically mitigates automated dictionary attacks on SSH.
- Automation: Dynamically updates firewall rules without manual intervention.
- Resilient Configuration: Using a .local override file ensures custom settings are not overwritten during package updates.
