# Firewall-Configuration
UFW Firewall Task - Linux VM

This document describes the process to configure and test UFW (Uncomplicated Firewall) on a Kali Linux virtual machine. The goal is to allow SSH traffic on port 22 and verify that the port is open.

Steps Performed

1. Install UFW
Update package lists and install UFW.
Command:
sudo apt update
sudo apt install ufw -y

2. Enable UFW
Activate the firewall to start managing rules.
Command:
sudo ufw enable

3. Allow SSH Port 22
Add a rule to permit incoming SSH connections.
Command:
sudo ufw allow OpenSSH
Alternative command:
sudo ufw allow 22/tcp

4. Verify UFW Status
Check current rules and policies to ensure SSH is allowed.
Command:
sudo ufw status verbose

5. Check SSH Service
Make sure the SSH service is running and enabled at startup.
Commands:
sudo systemctl start ssh
sudo systemctl enable ssh
sudo systemctl status ssh

6. Verify Port 22 Listening
Check if the system is actively listening for connections on port 22.
Command:
sudo ss -ltnp | grep :22

7. Test SSH Port Locally
Attempt to connect to port 22 from the same machine to verify it is open.
Command:
nc -vz 127.0.0.1 22

8. Verify SSH Port with Nmap
Scan the VM’s IP address from another machine to confirm port 22 is open externally.
Command:
nmap -p 22 <VM_IP>

Result
Port 22 was successfully allowed in UFW, the SSH service was running, and tests confirmed that the port was open and accessible.
