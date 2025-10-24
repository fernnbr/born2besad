# Part 1: Virtual Machine Creation
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


- Click Next
