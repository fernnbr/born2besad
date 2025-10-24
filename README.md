
<p align="center">

  # Critical Rules and Cautions

<p align="center">
  <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZWlqcG9wc3lmcjdoNTN0amcxNDRuZXFxZWsxNnBrMTZocjhhdDJlMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/eImrJKnOmuBDmqXNUj/giphy.gif">
</p></figcaption>
<p align="center">
  (Alert! Alert! Alert!) 
</p>



#### Here are the critical rules you MUST follow and where they appear in my step-by-step guide

## CRITICAL - Will Result in Grade 0

1. NO Graphical Interface ❌

- Rule: Installing X.org or any graphical server = automatic 0
- Where: ✅ Already covered in **Step 14**: Software Selection - only select SSH and standard utilities

## NO Snapshots During Evaluation ❌

- Rule: If snapshots are detected during defense = automatic 0

- Where: ⚠️ **Step 42** recommends creating a snapshot - **DELETE IT BEFORE EVALUATION**

(Action needed: Remove the snapshot I recommended, or don't create it at all)

## Signature Must Match ❌

- Rule: If signature.txt doesn't match your VM = automatic 0
- **Where: Not in my guide - NEW STEP NEEDED**
Action: After completing all configuration, generate the signature

## Missing Steps in My Guide
4. Hostname Modification During Defense

- Rule: You must be able to change the hostname during evaluation
- Where: Missing from my guide

Add after Step 8: Practice command ```hostnamectl set-hostname newhostname42```

## Creating New User During Defense

- Rule: You must create a new user and assign to a group during evaluation
- Where: Partially covered in Step 29-30, but needs practice

### Commands to know:

```
bash  sudo adduser newusername
sudo usermod -aG groupname newusername
```

## Stopping Monitoring Script Without Modifying It

- Rule: Must be able to stop the script during defense without editing it
- Where: Mentioned in Step 40 but not explained

### Commands to know:

```
bash  sudo systemctl disable cron    # Disable cron service
sudo systemctl stop cron       # Stop cron immediately
```

# Subject-Specific Requirements

### Operating System Choice

- Rule: Must use latest stable Debian (recommended) or Rocky
- Where: ✅ Covered in "Choosing Your Linux Distribution"
- Important: Be ready to explain why you chose Debian and differences between ```apt``` and ```aptitude```

### AppArmor Must Run at Boot (Debian)

- Rule: AppArmor must be running on startup
- Where: ⚠️ MISSING from my guide
- Add NEW Step after Step 25:

```
bash  sudo systemctl status apparmor    # Check status
sudo systemctl enable apparmor    # Ensure it starts at boot
```

### Firewall Must Be Active at Boot

- Rule: UFW must start automatically
- Where: ✅ **Covered in Step 25** (ufw enable does this)
Verify with: ```sudo systemctl status ufw```

### Root Password Must Follow Policy

- Rule: Root password must comply with the new policy (except the 7 different characters rule)
- Where: ✅ Covered in Step 37
(Note: Subject clarifies root doesn't need 7 different characters from old password)

</div>
---

<p align="center">

  # Part 1: Virtual Machine Creation

<p align="center">
  <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGEzd2M5eGF4dTdsc3Fsa29vcmYzeWFkbTdyczRwbDBjZGtmNjRobiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hrdX1BsUBq7DkGJCCd/giphy.gif">
</p></figcaption>
<p align="center">
  (Alert! Alert! Alert!) 
</p>


### Understanding Hypervisors
#### What is a hypervisor?

A hypervisor is software that allows you to create and run virtual machines.

Two types exist:

- Type 1 (Bare-metal): Runs directly on hardware (examples: VMWare ESXi, Microsoft Hyper-V, Proxmox) - used in servers
- Type 2 (Hosted): Runs on top of your existing operating system (examples: VirtualBox, VMware Workstation) - used on personal computers

For this study, we will use VirtualBox (a free, open-source Type 2 hypervisor).

### Choosing Your Linux DistributionYou have two options:

1) Rocky Linux: Successor to CentOS, robust for servers

   ```
   Rocky Linux is a free, enterprise-level Linux distribution designed as a replacement for CentOS. It’s built to be stable and secure, especially for business servers and datacenters.
   Debian and Rocky Linux are both stable Linux distributions, but they come from different worlds: Debian is an independent, community-driven system focused on flexibility and general use, using APT and .deb packages,
   while Rocky Linux is built from Red Hat Enterprise Linux, using DNF/YUM and .rpm packages, and is designed especially for enterprise servers and corporate environments.
   In short, Debian is ideal for beginners learning Linux basics and broad use cases, whereas Rocky Linux teaches you the structure and tools you’d find in large, professional IT infrastructures.
   ```
   
  
2) Debian: Extremely stable, foundation for Ubuntu

```
Debian is a Linux-based operating system, one of the oldest, most stable, and most widely used distributions. It’s like the “grandparent” of many others (Ubuntu, for example, is built from Debian).
Debian is reliable, well-documented with tons of guides (like game wikis), and hard to break compared to "hardcore mode" distros like Arch.
Perfect for learning server management without ragequitting!

It's used on Servers (super reliable), Development environments, Learning Linux fundamentals, Virtual machines for practice and testing
and it's known for stability, security, and a huge collection of software packages.
```

Recommendation: Choose Debian if you're new to system administration.

</div>

---

<p align="center">

# Part 2: Downloading and Setting Up VirtualBox

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTFoczQweHN1ZXA1MmRkZWhhdGlqaWo4eXA2emM4YmtycjBpcjF1NSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hVVJisUlKBgQYc6PQh/giphy.gif">
</p></figcaption>
<p align="center">
  (Alert! Alert! Alert!) 
</p>

## Step 1: Download Debian ISO

- Go to Debian's official website (https://www.debian.org/distrib/netinst)
- Download the latest ISO image 
- Select the "amd64" architecture
- Save the file to a location you'll remember

## Step 2: Create Your Virtual Machine

- Open VirtualBox
- Click the "New" button

#### Configure the following:

- Name: Choose a name for your VM (e.g., "born2beroot")
- ISO Image: Select the Debian ISO you just downloaded

#### Storage Location:

- sgoinfre folder (30 GB available)
(Home directory only has 5 GB, which is insufficient)

- (!) IMPORTANT: Check ✅ "Skip Unattended Installation"

</div>

---

Part 3: Installing the Operating System
Step 5: Boot the Virtual Machine

In VirtualBox, select your VM
Click "Start"
The VM will boot from the Debian ISO

Step 6: Begin Debian Installation

When the boot menu appears, select "Install" (not "Graphical Install")
Press Enter

Step 7: Language and Location

Select your language (e.g., English)
Select your location (e.g., United States)
Select your keyboard layout (e.g., American English)

Step 8: Network Configuration

Hostname: Enter your login followed by 42 (e.g., chlimous42)

This is required by the project guidelines
This is the name of your device on the local network


Domain name: Leave this blank (just press Enter to skip)

Step 9: User Account Setup

Root password:

Enter a strong password for the root user
Confirm the password
Write this password down somewhere safe!


New user account:

Full name: Enter your login (e.g., chlimous)
Username: Enter your login again (e.g., chlimous)
Password: Enter a password for your user account
Confirm the password
Write this password down too!



Step 10: Disk Partitioning (IMPORTANT)

Select "Guided - use entire disk and set up encrypted LVM"
Select your disk (usually only one option available)
Select "Separate /home, /var and /tmp partitions"

This is required for the bonus part


Select "Yes" to write changes to disk
Encryption password:

Enter a strong password for disk encryption
Confirm the password
Write this password down! You'll need it every time you boot


Volume group size:

When asked how much space to use, do NOT use all available space
Leave some space for additional logical volumes (about 2-3 GB)
Example: If you have 20 GB, use only 17 GB


Select "Finish partitioning and write changes to disk"
Select "Yes" to confirm

Step 11: Configure Logical Volume Manager (LVM)

Select "Configure the Logical Volume Manager"
Select "Yes" to write changes
Create first logical volume:

Select "Create logical volume"
Select the volume group (usually named something like "debian-vg")
Name: srv
Size: 1 GB (or press Enter for suggested size)


Create second logical volume:

Select "Create logical volume" again
Select the volume group
Name: var-log
Size: Use remaining space


Select "Finish"

Step 12: Format the New Logical Volumes

Find the /srv partition in the list:

Select it
Choose "Use as: Ext4 journaling file system"
Set "Mount point: /srv"
Select "Done setting up the partition"


Find the /var-log partition in the list:

Select it
Choose "Use as: Ext4 journaling file system"
Set "Mount point: Enter manually"
Type: /var/log
Select "Done setting up the partition"


Select "Finish partitioning and write changes to disk"
Select "Yes" to confirm

Step 13: Package Manager Configuration

Scan extra installation media: Select "No"
Debian archive mirror country: Select your country
Debian archive mirror: Select the default (first option)
HTTP proxy: Leave blank, press Enter
Package usage survey: Select "No"

Step 14: Software Selection

Use Space bar to check/uncheck options
ONLY select the following:

✅ SSH server
✅ standard system utilities


Uncheck everything else (including "Debian desktop environment")
Press Enter to continue
Wait for installation to complete

Step 15: GRUB Bootloader

Install GRUB: Select "Yes"
Device: Select your disk (usually /dev/sda)
Wait for installation to finish

Step 16: Complete Installation

Select "Continue" to reboot
Remove the installation media (VirtualBox does this automatically)
The VM will reboot
Enter your encryption password when prompted
You should see a login prompt


Part 4: Initial Login and SSH Setup
Step 17: First Login

At the login prompt, type: root
Press Enter
Type the root password you created earlier
Press Enter
You should now see a command prompt like: root@chlimous42:~#

Step 18: Check SSH Service

Run the following command to check SSH status:

bash   systemctl status ssh

Note: The output should show "active (running)" and "Listening on 0.0.0.0 port 22"
Press q to exit the status view

Step 19: Configure SSH Port

Open the SSH configuration file:

bash   nano /etc/ssh/sshd_config
```
   - **Note**: `nano` is a text editor. Use arrow keys to navigate
2. Find the line that says `#Port 22`
   - Use arrow keys to navigate to this line
3. Change it to:
```
   Port 4242
```
   - Remove the `#` at the beginning (uncomment)
   - Change `22` to `4242`
4. Find the line that says `#PermitRootLogin prohibit-password`
5. Change it to:
```
   PermitRootLogin no

Remove the # at the beginning
Change prohibit-password to no


Save and exit:

Press Ctrl + O (to save)
Press Enter (to confirm filename)
Press Ctrl + X (to exit)



Step 20: Restart SSH Service

Run the following command:

bash   systemctl restart ssh

Verify the change:

bash   systemctl status ssh

Note: It should now show "Listening on 0.0.0.0 port 4242"
Press q to exit

Step 21: Configure Port Forwarding in VirtualBox

Log out of the VM:

bash   logout

In VirtualBox, right-click your VM
Select "Settings"
Go to "Network"
Click "Advanced" (expand the section)
Click "Port Forwarding"
Click the "+" button (add new rule)
Configure the rule:

Name: SSH
Protocol: TCP
Host IP: Leave blank
Host Port: 2222 (at 42 Paris, port 22 is unavailable)
Guest IP: Leave blank
Guest Port: 4242


Click "OK" twice to save and close

What does this do?

Port forwarding tells VirtualBox to listen on port 2222 of your host machine
Any connection to port 2222 gets forwarded to port 4242 inside the VM
This allows you to SSH into your VM from your host terminal

Step 22: Test SSH Connection

Start your VM again
Enter your encryption password
Do NOT log in to the VM console
Open a terminal on your host machine (your actual computer)
Type the following command (replace chlimous with your username):

bash   ssh chlimous@localhost -p 2222

If asked "Are you sure you want to continue connecting?", type yes and press Enter
Enter your user password
You should now be connected via SSH!


Part 5: Firewall Configuration
Step 23: Switch to Root User

In your SSH session, switch to root:

bash   su -

Enter the root password
Note: The - after su loads root's environment

Step 24: Install UFW (Uncomplicated Firewall)

Install UFW:

bash   apt install ufw

When asked "Do you want to continue? [Y/n]", press Enter (or type y)
Wait for installation to complete

Step 25: Configure Firewall Rules

Set default policy to deny incoming traffic:

bash   ufw default deny incoming

What this does: Blocks all incoming connections by default


Set default policy to allow outgoing traffic:

bash   ufw default allow outgoing

What this does: Allows all outgoing connections (so you can browse, update, etc.)


Allow SSH port:

bash   ufw allow 4242

IMPORTANT: This ensures you can still connect via SSH
Without this, you would be locked out!


Enable the firewall:

bash   ufw enable

When asked "Command may disrupt existing ssh connections. Proceed with operation (y|n)?", type y and press Enter
Verify the firewall status:

bash   ufw status

Note: Should show "Status: active" and "4242 ALLOW Anywhere"


Part 6: Installing and Configuring sudo
Step 26: Install sudo

Make sure you're logged in as root (if not, run su -)
Install sudo:

bash   apt install sudo

Press Enter to confirm
Wait for installation to complete

Step 27: Configure sudo Settings

Open the sudo configuration file:

bash   visudo
```
   - **Note**: This opens the file in a safe editor that checks for syntax errors
2. The file will open. Use arrow keys to navigate
3. Find the line that says:
```
   Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
```
   - **Note**: This line should already exist. Leave it as is.
4. Add the following lines **after** the `secure_path` line:
```
   Defaults requiretty
   Defaults badpass_message="WRONG PASSWORD"
   Defaults logfile="/var/log/sudo/sudo.log"
   Defaults log_input
   Defaults log_output
   Defaults iolog_dir=/var/log/sudo
   Defaults passwd_tries=3
What each line does:

requiretty: Requires a terminal (TTY) to use sudo
badpass_message: Custom message when wrong password is entered
logfile: Where to save sudo logs
log_input: Log all commands entered with sudo
log_output: Log all output from sudo commands
iolog_dir: Directory for input/output logs
passwd_tries: Maximum number of password attempts (3)


Save and exit:

Press Ctrl + O (to save)
Press Enter
Press Ctrl + X (to exit)



Step 28: Create sudo Log Directory

Create the log directory:

bash   mkdir -p /var/log/sudo

Note: -p creates parent directories if needed


Part 7: Group Management
Step 29: Create user42 Group

Create the user42 group:

bash   groupadd user42

Note: This is required by the project

Step 30: Add Your User to Groups

Add your user to user42 and sudo groups (replace chlimous with your username):

bash   usermod -a -G user42,sudo chlimous
What this command does:

usermod: Command to modify a user
-a: Append (add without removing from other groups)
-G user42,sudo: Add to these groups
chlimous: The username

Step 31: Verify Group Membership

Check the groups file:

bash   cat /etc/group

Look for lines containing:

user42:x:1001:chlimous
sudo:x:27:chlimous


Note: Your user should appear in both groups

Step 32: Test sudo Access

Log out from root:

bash   exit

You should now be back as your regular user
Test sudo by running:

bash   sudo ls

Enter your user password (not root password)
If it works, you'll see a directory listing
Note: You now have sudo privileges!


Part 8: Password Policy Configuration
Step 33: Configure Password Aging

Switch to root:

bash   su -

Open the login definitions file:

bash   nano /etc/login.defs

Find and modify these lines:

Find: PASS_MAX_DAYS    99999
Change to: PASS_MAX_DAYS    30
Find: PASS_MIN_DAYS    0
Change to: PASS_MIN_DAYS    2
Find: PASS_WARN_AGE    7
Leave as: PASS_WARN_AGE    7



What these settings mean:

PASS_MAX_DAYS: Password expires after 30 days
PASS_MIN_DAYS: Must wait 2 days before changing password again
PASS_WARN_AGE: Warning given 7 days before expiration


Save and exit (Ctrl+O, Enter, Ctrl+X)

Step 34: Apply Policy to Existing Users

Apply to your user (replace chlimous with your username):

bash   chage -M 30 chlimous
   chage -m 2 chlimous

Apply to root user:

bash   chage -M 30 root
   chage -m 2 root
What these commands do:

chage: Change password aging information
-M 30: Set maximum days to 30
-m 2: Set minimum days to 2

Step 35: Install Password Quality Module

Install libpam-pwquality:

bash   apt install libpam-pwquality

Press Enter to confirm
Wait for installation to complete

Step 36: Configure Password Quality Rules

Open the PAM configuration file:

bash   nano /etc/pam.d/common-password
```
2. Find the line:
```
   password    requisite    pam_pwquality.so retry=3
```
3. Replace it with:
```
   password    requisite    pam_pwquality.so retry=3 minlen=10 difok=7 maxrepeat=3 dcredit=-1 ucredit=-1 lcredit=-1 reject_username enforce_for_root
What each parameter means:

retry=3: Maximum 3 incorrect attempts
minlen=10: Minimum password length is 10 characters
difok=7: At least 7 characters must be different from old password
maxrepeat=3: Maximum 3 consecutive identical characters
dcredit=-1: Minimum 1 digit required (negative = minimum)
ucredit=-1: Minimum 1 uppercase character required
lcredit=-1: Minimum 1 lowercase character required
reject_username: Username cannot be in password
enforce_for_root: These rules apply to root too


Save and exit (Ctrl+O, Enter, Ctrl+X)

Step 37: Update Passwords with New Policy

Change your user password (replace chlimous with your username):

bash   passwd chlimous

Enter a new password that meets all requirements:

At least 10 characters
At least 1 uppercase letter
At least 1 lowercase letter
At least 1 digit
Cannot contain your username
At least 7 characters different from old password
No more than 3 consecutive identical characters


Confirm the new password
Change root password:

bash   passwd root

Enter a new password that meets all requirements
Confirm the new password

Note: If the password doesn't meet requirements, you'll get an error message. Keep trying until you create a valid password.

Part 9: Monitoring Script
Step 38: Install Required Packages

Make sure you're logged in as root
Install bc (calculator) and sysstat (system statistics):

bash   apt install bc sysstat

Press Enter to confirm
Wait for installation to complete

Step 39: Create the Monitoring Script

Create the directory for the script:

bash   mkdir -p /etc/cron.d

Create the script file:

bash   nano /etc/cron.d/monitoring.sh

Write your monitoring script in this file

Note: The document mentions checking a reference script but doesn't include it
Your script should collect system information like:

Architecture and kernel version
Physical and virtual processors
RAM usage
Disk usage
CPU load
Last boot time
LVM status
Active connections
Number of users
Network IP and MAC address
Number of sudo commands executed




Save and exit (Ctrl+O, Enter, Ctrl+X)
Make the script executable:

bash   chmod +x /etc/cron.d/monitoring.sh
Step 40: Configure Cron Job

Open the root crontab:

bash   crontab -e
```
2. If asked to select an editor, choose `1` (nano)
3. Add this line at the end of the file:
```
   */10 * * * * bash /etc/cron.d/monitoring.sh | wall
What this line means:

*/10: Every 10 minutes
* * * *: Every hour, every day, every month, every day of week
bash /etc/cron.d/monitoring.sh: Execute the monitoring script
| wall: Send output to all logged-in users


Save and exit (Ctrl+O, Enter, Ctrl+X)
Note: The script will now run automatically every 10 minutes

Step 41: Test the Monitoring Script

Run the script manually to test:

bash   bash /etc/cron.d/monitoring.sh

Check if the output appears correctly
Wait 10 minutes and verify the script runs automatically


Part 10: Final Steps
Step 42: Create a Snapshot (Recommended)

Shut down your VM:

bash   shutdown -h now

In VirtualBox, select your VM
Click "Snapshots" (top right)
Click the "Take" button (camera icon)
Name: After full configuration
Click "OK"
Why?: If something breaks later, you can restore to this point

Step 43: Verify All Requirements
Before your evaluation, check:

 VM runs without graphical interface
 SSH works on port 4242
 UFW firewall is active with only port 4242 allowed
 Hostname is your login + 42
 User is in user42 and sudo groups
 Password policy is enforced
 Sudo is properly configured
 Monitoring script runs every 10 minutes
 Partitions include separate /home, /var, /tmp, /srv, and /var/log
 LVM is encrypted

Step 44: Practice for Evaluation
Practice these commands for your evaluation:
bash# Check OS
uname -a

# Check groups
groups

# Check sudo logs
sudo cat /var/log/sudo/sudo.log

# Check firewall
sudo ufw status

# Check SSH
sudo systemctl status ssh

# Check partitions
lsblk

# Check password policy
sudo chage -l username

Congratulations! 🎉
Your Born2beroot virtual machine is now fully configured and ready for evaluation!
Important reminders:

Keep your passwords written down safely
Remember your encryption password (needed at every boot)
Don't modify the VM after taking your snapshot
Practice explaining what each configuration does

Good luck with your evaluation! 




- Click Next
