
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

# Part 2: Downloading and Setting Up VirtualBox

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


---




- Click Next
