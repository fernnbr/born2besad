# Born2beSad | Welcome, Stranger (to the world of VM) 
I hope to help you to suffer less with that that I do. 
You're welcome. 

This guide also contains gifs. 
To help you to laugh between one or two crying outbursts. 

```
“A computer terminal is not some clunky old television with a typewriter in front of it.
It is an interface where the mind and body can connect with the universe and move bits of it about.”
```

# Virtual Machine 
#### A really step by step guide 

I'll guide you through the steps of setting your VM! 
Sharing the knowledge shared with me by many at the community onilne and in person. 
Please, save at least 5 hours to do this in a confy way. 

# Downloading Debian (yeah, we'll not Rocky you) 

---

# Installing 

<div align="center">
<p align="center">
  <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMnZhZWF4d3d5NnN3Z24wM3RrM3ZyZzc2NThma3JwZXVnbzQ4eWVuNiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11Cn7h5PA8cyiY/giphy.gif">
</p></figcaption>
<p align="center">
  (weeeeeee...)
</p>
</div>

- We will be using Virtualbox
- Download Debian (amd64) at https://www.debian.org/distrib/netinst
- Open up Virtualbox and click "New"
- Name your virtual machine (remember to take a picture or take notes of the name)
- Choose the downloaded ISO image (debian),
- Select a storage location for the data (sgoinfre)
- Check "Skip Unattended Installation"
- Allocate at least 8 GiB of RAM (1000 Mb) and 8 vCPU cores
- Click Next
- Allocate 10 Gb in Disk Size
- Click "Pre-Allocate Full Size"
- Click Next
- Click Finish

### Time to install the operating system (Click "Start" on your Virtualbox interface)

- Select "Install" and then follow the on-screen instructions
- Set the hostname as your login followed by 42 (i.e.: user42) (This is the name of your device on the local network)
- Skip domain name configuration
- Set a password for root
- Make a user with your login and set a password for this account
- Select "Guided - use entire disk and set up encrypted LVM" [Option 03]
- Partition disks: Select "Separate /home partition"
- Click "Yes"
- Wait
- Type a strong password (min 10 char len, with lower and upper char, numbers and special char) 
- Amount of volume: type "max"; then click "continue"
- Click "Finish Partitioning and Write Changes"
- Click "Yes"
- Wait
- Click "No"
- Click "Debian.org" option
- Click Continue
- Wait
- Click "No" for the Survey
- Now select only "SSH Server" and "standard system utilities"
- Click "Yes" to install the GRUB loader
- Select /dev/sda (ata-VBOX...)
- Confirm reboot (select "Yes")

---

# Server Configuration

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWNxOXRxaWZtbzFudWFsMnM4eG9jNGh5aHM2OHd6a2xwOGthYTNpcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/tczJoRU7XwBS8/giphy.gif">
</p></figcaption>
<p align="center">
</p>

- login
- clear
- type "su -"
- type password
- type "apt update"
- type clear
- type apt install sudo
- clear
- type "add user (your user) sudo"
- type "getent group sudo"
- type "reboot"
- type "clear"
- type "sudo -V"
- type "sudo visudo"
- type the settings (retry, badpass message)
- save (ctrl+X)
- type "sudo mkdir" -p / var/log/sudo/ 
- clear
- type "sudo touch /var/log/sudo/sudo.log"
- clear

---

# Installing and Configuring SSH 

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExbXNwMTlmZHpuNnBhamphZGowcHg2ZHM1azRjb2VudXd0Zmk1dm9zMiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/S0hxMGYFhEMzm/giphy.gif">
</p></figcaption>
<p align="center">
</p>

- type "sudo apt install openssh-server -y"
- clear
- sudo nano /etc/ssh/sshd_config
- Go to "Port"
- Type "4242"
- Then delete "Permit Root Login"
- Write "PermitRootLogin no"
- save (ctrl+X) 
- clear

---

# Optional

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExZzNnNWhldWtoMXRib3ZlMDVpZXgydXNzY2lsNzc5dmZ6MWRvdWNxbCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/T2qfJTEEfe4AU/giphy.gif">
</p></figcaption>
<p align="center">
</p>

- type sudo nano /etc/ssh/ssh_config
- save (ctrl+X) 
- clear
- type "sudo service ssh status"

---

# Installing and Configurin UFW

<p align="center">
  <img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWVxb2g1cThmNDQzemlveDNkY2FpcjU4aTRiNXRyYnNoM2lmNnkzcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/AwrtP9lMXtXiM/giphy.gif">
</p></figcaption>
<p align="center">
</p>

- type "sudo apt install ufw -y"
- wait
- clear
- type "sudo ufw enable"
- type "sudo ufw allow 4242"
- sudo ufw status

---

# Connecting to the VM via SSH 

<p align="center">
  <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ2d4eXZxOXdkZW40MTdhdTBubWZmaWMzMDM5emJhZG1qa3Y1cXlsMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/gMfyVpJGHn0DDCZAUK/giphy.gif">
</p></figcaption>
<p align="center">
</p>

- ssh (your username)@(your IP) -p 4242
(In case of error try see your ip with ip a; if the error persists, shut down the VM; then open it again;
then sleect your VM; then go to settings; then go to network; then change NAt to bridge; then use ip a again; then get the IP and redo the ssh step)\



--
--->>>> (continue from here)

# SSH connection from Outside 
#### To check if the terminal is listening 

- type "netstat -tuln | grep 4242"
- ssh (your username)@(your IP) -p 4242
- ssh (your username)@(your IP) -p 4241
- type "exit"
- type "netstat -tuln | grep 4241"

---

# Password Policy

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExYjN1N2tqbmtobzZqN2h4dGhleWt2eTZqa2kzZzByYTd1Zmh1bHN6cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11fot0YzpQMA0g/giphy.gif">
</p></figcaption>
<p align="center">
</p>


- sudo nano /etc/login.defs
- type your password
- Go to PASS_MAX_DAYS and change it to 30
- Go to PASS_MIN_DAYS and change it to 2
- clear

---

### Install the Password Quality Checking Lib


<p align="center">
  <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExNDdwNW56MWluZmhwenZ2dWFnNnJkeWRpcGN3aTdocnoyd3p5Z2VjbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/YGlRW1Am9q7e0/giphy.gif">
</p></figcaption>
<p align="center">
</p>


- type "sudo apt-get install libpam-pwquality -y"
- Wait
- clear
- type "sudo nano /etc/pam.d/common-password"
- Go to password requisite pam_pwquality.so retry=3 and add after it: minlen=10 ucredit=-1 lcredit=-1 dcredit=-1 maxrepeat=3 reject_username difok=7 enforce_for_root
- Save (ctrl+X) 
- Clear
- type "sudo reboot"
- Unlock VM

---

# Update the old login to comply with the password policy


<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ3d2M29xdTR5NDg5d3F3aHpqdGxlMHh6ejNpcWp4eTAxejlkM3V3cyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/PPOLUsngQy68nx8tfp/giphy.gif">
</p></figcaption>
<p align="center">
</p>


- type "passwd"
- Type your current password
- Type your new password
- Clear
- type "sudo chage -l (your user)"
- Type your password
- See the log of password changes info
- Type "sudo chage -M 30 -m 2 -W 7 (your user)" (to change the config)
- Clear

---

# Update the old root password to comply the policy 


<p align="center">
  <img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcTk0OTVsbXllazVhcHFrMmtjMHNiNWUxdnJmenFvcm1lNjYycDE4cSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/DXC8bM9ZM4Wn3PDvK7/giphy.gif">
</p></figcaption>
<p align="center">
</p>


- type "sudo passwd root"
- sudo chage -l root
- sudo chage -M 30 -m 2 -W 7 root (to change the config)
- sudo chage -l root (to check the changes)
- clear

---

# Creating Users and Groups 


<p align="center">
  <img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExYXBqdTI0Y2IyNGJyd2ltdGQ2dWh0MWhyaXI3NWR4a3A2ZGpvZmVvdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Q86ySOsoUKl2KUm23o/giphy.gif">
</p></figcaption>
<p align="center">
</p>


- type "sudo adduser new_user"
- type new password
- clear
- type "getent passwd new_user"
- clear
- type "sudo addgroup user42"
- type "sudo addgroup evaluating"
- type "sudo adduser (your user42)"
- type New Password
- clear
- type "sudo adduser (your user) user42"
- type "sudo add user (your user) evaluating"
- clear
- type "getent group user42"
- type "getent group evaluating"

---

# Crontab Config


<p align="center">
  <img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExdHE3ZzUycXVzNnM0eHRhenkwYzJ4am00eDJxd2s3OHJ2ZHRyNnpvayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/dxP9yzCvWre2XLoPfx/giphy.gif">
</p></figcaption>
<p align="center">
</p>


- type "sudo touch /usr/local/bin/monitoring.sh"
- type "sudo chmod 755 /usr/local/bin/monitoring.sh"
- type "sudo nano /usr/local/bin/monitoring.sh"
- A blank window will open
- Add the following script:

```
#!/bin/bash

# Architecture
arch=$(uname -a)

# CPU physical
pcpu=$(grep "physical id" /proc/cpuinfo | sort | uniq | wc -l)

# CPU virtual
vcpu=$(grep "processor" /proc/cpuinfo | wc -l)

# RAM
ram_total=$(free -m | awk '$1 == "Mem:" {print $2}')
ram_use=$(free -m | awk '$1 == "Mem:" {print $3}')
ram_percent=$(free -m | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}')

# DISK
disk_total=$(df -BG | grep '^/dev/' | grep -v '/boot$' | awk '{disk_t += $2} END {print disk_t}')
disk_use=$(df -BM | grep '^/dev/' | grep -v '/boot$' | awk '{disk_u += $3} END {print disk_u}')
disk_percent=$(df -BG | grep '^/dev/' | grep -v '/boot$' | awk '{disk_u += $3} {disk_t+= $2} END {printf("%d"), disk_u/disk_t*100}')

# CPU load
cpul=$(grep 'cpu ' /proc/stat | awk '{usage=($2+$4)*100/($2+$4+$5)} END {printf("%.1f", usage)}')

# Last boot
lb=$(who -b | awk '$1 == "system" {print $3 " " $4}')

# LVM use
lvmu=$(if lsblk -o TYPE | grep -lq "^lvm$"; then echo yes; else echo no; fi )

# TCP connections
ctcp=$(ss -Ht state established | wc -l)

# User log
ulog=$(users | wc -w)

# Network
ip=$(hostname -I | awk '{print $1}')
mac=$(ip link show | grep "ether" | awk '{print $2}')

# Sudo
cmnd=$(journalctl _COMM=sudo | grep COMMAND | wc -l)

wall "Architecture: $arch
#CPU physical : $pcpu
#CPU virtual : $vcpu
RAM total : ${ram_total}MB
RAM used : ${ram_use}MB ($ram_percent%)
Disk total : ${disk_total}G
Disk used : ${disk_use}G (${disk_percent}%)
CPU load : ${cpu1}%
Last boot : $lb
LVM use : $lvmu
TCP connections : $ctcp
User log : $ulog
Network : IP $ip ($mac)
Sudo : $cmnd commands"
```

- Save (ctrl+X) 
- type "sudo visudo"
- Go to %sudo ALL=(ALL:ALL) ALL
- Below it type: "(your user) ALL=(ALL) NOPASSWD:/usr/local/bin/monitoring.sh"
- Save (ctrl+X)
- Clear
- type "sudo systemctl enable cron.service"
- clear
- type "sudo reboot"
- login to your VM
- clear

---

# Test Run the Script

<p align="center">
  <img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXBlMGdxNG91YTZuNGJjajMzYWI5eWo5dm52MXl4dWtqZ3RwbDllayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/CUbiYQbsKSGAM/giphy.gif">
</p></figcaption>
<p align="center">
</p>

- type "sudo crontab-u root -e"
- type your password
- type/choose "1"
- go to the EOF (End of the File) and type: "*/10 * * * * /usr/local/bin/monitoring.sh" (to run the script every 10 min)
- Save (ctrl+X)

---

# Generating Signature .txt

<p align="center">
  <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExbWZseWxma2VhY2diN3B2dHE0eHd2ZngxdThxZDVseWpvMW41d28wNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3orieOSehVQs29STDi/giphy.gif">
</p></figcaption>
<p align="center">
</p>

- **power off the VM before generating the signature to avoid changing the disk image**
- on your host machine **(not inside byour Virtual Machine)** navigate to where your .vdi file is stored (cd mnt/nfs/homes/(youruser)/sgoinfre/(name of the project))
- Generate the SHA-1 checksum (shasum (nameoftheproject).vdi)
- Wait
- Copy the resulting hash into a file named **signature.txt**
- **Do not start the VM again** unless you are ok with changing the signature
- If you need more changes, or clone the VM or keep a snapshot

---


#### Credits: Many thanks to Nirmal Gope and all the colleagues that helped a lot 

<p align="center">
  <img src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExa2lhbDRrcDB2ZWJncjVuOTdjMjAzcDdidW8zbjhxeXliNDQwZWl6cSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/WKdPOVCG5LPaM/giphy.gif">
</p></figcaption>
<p align="center">
</p>


---

# To know more | To study 

<p align="center">
  <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExa2RwbWw0bXF5bTE3MXJybTl1MmQweDRobGxmNGlzNHo2eG95ZXJseiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/H48YKEw3fXrcvIF2xE/giphy.gif">
</p></figcaption>
<p align="center">
  (ommmmmmggggggg...)
</p>

## How a Virtual Machine Works

<p align="center">
  <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExNDg4dGF4eWtmOWdnbXEzd2I0dXJhemJ4eWVpb2hrdXNmY2xoZWpraCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/mcsPU3SkKrYDdW3aAU/giphy.gif">
</p></figcaption>
<p align="center">
</p>

A **virtual machine (VM) is a software-based emulation of a physical computer that runs on a host system**. 

It **works through a layer called a hypervisor** (or Virtual Machine Monitor), which sits between the hardware and the virtual machines. 
The hypervisor allocates physical resources, like **CPU, memory, storage, and network—to each VM and manages their execution**.

There are **two types of hypervisors**:

- **Type 1 (bare-metal)**: Runs directly on hardware (e.g., VMware ESXi, Hyper-V)
- **Type 2 (hosted)**: Runs on top of an operating system (e.g., VirtualBox, VMware Workstation)

Each VM includes a complete operating system (guest OS) and applications, isolated from other VMs on the same host. 

The **hypervisor translates the VM's instructions to the physical hardware**, creating the **illusion that each VM has dedicated resources**. 
This isolation means VMs are independent—if one crashes, others continue running unaffected.

## CentOS vs DebianCentOS 

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExejZ4OXoycDB2eG5jdGw1dnppeTNmNDZ5dXg0c3gzYmJkbGp5dWt2aSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qP493R1PqZi44u4kKl/giphy.gif">
</p></figcaption>
<p align="center">
</p>

Both are popular Linux distributions but serve different philosophies and use cases. 

- **CentOS (now CentOS Stream)** is based on Red Hat Enterprise Linux (RHEL) and uses the RPM package management system with YUM/DNF package managers.
It **focuses on enterprise stability with longer release cycles and extended support periods**.

- **Debian, on the other hand, is an independent, community-driven** distribution known for its **stability and vast software repositories**.

It uses the DEB package format with APT package managers and offers three branches:
Stable, Testing, and Unstable, giving users more flexibility in choosing between stability and cutting-edge features.

## Purpose of Virtual Machines 

<p align="center">
  <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExNnlqd2hiNmp1bDltb2J1OTYyOHdnZ3loNTBhY20zazBwdGswdjR1MyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/urvsFBDfR6N32/giphy.gif">
</p></figcaption>
<p align="center">
</p>

Virtual machines serve several critical purposes in modern computing:

- **Server Consolidation**: Multiple VMs can run on a single physical server, maximizing hardware utilization and reducing costs
  
- **Isolation and Security**: VMs provide sandboxed environments, preventing software conflicts and containing security breaches
  
- **Development and Testing**: Developers can create identical environments for testing without affecting production systems
  
- **Legacy Application Support**: Old software can run on older OS versions within VMs on modern hardware
  
- **Disaster Recovery**: VMs can be easily backed up, cloned, and migrated between hosts
  
- **Cloud Computing**: VMs form the foundation of cloud infrastructure, enabling scalable, on-demand computing resources

## APT vs AptitudeAPT (Advanced Package Tool) and Aptitude (https://youtu.be/i_SsnRdgitA?si=RcNbo9RApzX-4aui)

<p align="center">
  <img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExdGJkc2ppM2FyZ253eGg0YmFxZTF4ZDhmNnZidW9mY20wdTB0Yzl0YyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/asI6WBJXOn30I/giphy.gif">
</p></figcaption>
<p align="center">
</p>

Both are **package management tools for Debian-based systems**, but they differ in functionality and interface. 

- **APT is a command-line tool** that provides **basic package management functions** (install, remove, update) and is the lower-level tool that other package managers build upon. 

- **Aptitude is a higher-level interface** that includes both a **text-based interactive UI and command-line functionality**.

It offers more sophisticated dependency resolution, can automatically handle orphaned packages, and provides features like package search with filtering. 

While **APT is simpler and faster for basic operations, Aptitude is more powerful for complex package management scenarios**, 
though modern versions of APT have incorporated many of Aptitude's improvements.

## AppArmorAppArmor (Application Armor) 

<p align="center">
  <img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExdG8zdmRmejVtdTg2NGNuczFudHB3emo0a2xqdjRxM3l3eTAycXF2dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7btNjXRumA5KHOCs/giphy.gif">
</p></figcaption>
<p align="center">
</p>

is a **Linux security module that implements mandatory access control (MAC) to restrict programs' capabilities and access to system resources**. 

It works by assigning security profiles to applications that define what files they can access, what capabilities they have, and what network operations they can perform. 
Unlike SELinux, **AppArmor uses file paths rather than labels**, making it simpler to configure and understand. 

Profiles can run in either enforcement mode (blocking violations) or complain mode (logging violations without blocking). 

AppArmor is particularly popular in Ubuntu and SUSE distributions, 
**providing an additional layer of defense by limiting the damage that compromised applications can cause**, 
even if they're running with elevated privileges.

## Advantages of a Strong Password

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNnFjMjFzdGtzOTA3ejduZm9mbmlrN3JudDQ3ZTd4bzcwMGlyeTZtbCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/fq6xyKgDC0eAE2ezxV/giphy.gif">
</p></figcaption>
<p align="center">
</p>

A **strong password is your first line of defense against unauthorized access to your accounts and systems**. 

Strong passwords—those that are long (12+ characters), complex (mixing uppercase, lowercase, numbers, and symbols), and unique for each account—are exponentially harder 
for attackers to crack through brute force or dictionary attacks. 

They protect against automated hacking tools that can try millions of password combinations per second. 

A compromised weak password can lead to data breaches, identity theft, financial loss, and unauthorized access to sensitive information. 

Additionally, strong passwords reduce the risk of credential stuffing attacks, 
where hackers use stolen passwords from one breach to access other accounts.

## UFW (Uncomplicated Firewall)

<p align="center">
  <img src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2czbzNyeHRseTBmY3M2amdibmhqZWRpenBvcXZkdG91Z3d4ZXgyNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/5GuExKmluBdrrtAFwk/giphy.gif">
</p></figcaption>
<p align="center">
</p>

**UFW is a user-friendly command-line interface for managing firewall rules on Linux systems**, specifically designed as a simplified frontend for iptables. 

**It allows administrators to easily configure which network ports are open or closed**, control incoming and outgoing traffic, and set up rules without dealing with the complexity of raw iptables syntax. 

**UFW is particularly useful because it provides a straightforward way to secure your system by blocking unwanted connections** while allowing legitimate traffic. 

For example, you might allow SSH on port 22 while blocking all other incoming connections. 
It's especially valuable for server security, helping prevent unauthorized access 
and protecting against network-based attacks by implementing a default-deny policy and only opening specific ports as needed.

## SSH (Secure Shell)

<p align="center">
  <img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExcG5naWY3MnAxbWZnMTEwc3gxeGMwdjlzYTFoeDBreXRhc3R2dHVqaCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/14ezDpib8JS04E/giphy.gif">
</p></figcaption>
<p align="center">
</p>

**SSH is a cryptographic network protocol used for secure remote access and management of computers over unsecured networks**. 

It provides **encrypted communication between a client and server**, allowing you to **securely log into remote machines, execute commands, transfer files, and tunnel other network services**. 

SSH replaces insecure protocols like Telnet and FTP by encrypting all data, including passwords, preventing eavesdropping and man-in-the-middle attacks. 

It's essential for **system administrators managing servers, developers accessing remote development environments, and anyone needing secure remote connectivity**. 
SSH uses public-key cryptography for authentication, allowing passwordless login through key pairs, which is both more secure and convenient than password-based authentication.

## Cron

<p align="center">
  <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ2ZhdXJrc2hzcXhkNXk0ZHl2am54dHI4Y3BudDRkYmc2YWd0a2diZSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/fKYdL6Sb3gnJJyrQ7z/giphy.gif">
</p></figcaption>
<p align="center">
</p>

**Cron is a time-based job scheduler in Unix-like operating systems that automatically executes commands or scripts at specified intervals**. 

Users create "cron jobs" by editing a crontab (cron table) file, which contains scheduling information 
**in a specific format: minute, hour, day of month, month, day of week, followed by the command to execute**. 

Cron is invaluable for **automating repetitive tasks such as system backups, log rotation, database maintenance, sending scheduled emails, running updates, or executing monitoring scripts**. 

For example, you could schedule a backup script to run every night at 2 AM, or have a cleanup script run every Sunday. 
The cron daemon runs continuously in the background, checking every minute whether any scheduled jobs need to be executed, making it an essential tool for system automation and maintenance.


