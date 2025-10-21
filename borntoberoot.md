1. We will be using Virtualbox
2. Download Debian (amd64) at https://www.debian.org/distrib/netinst
3. Open up Virtualbox and click "New"
4. Name your virtual machine (remember to take a picture or take notes of the name)
5. Choose the downloaded ISO image (debian),
6. Select a storage location for the data (sgoinfre)
7. Check "Skip Unattended Installation"
8. Allocate at least 8 GiB of RAM (1000 Mb) and 8 vCPU cores
9. Click Next
10. Allocate 10 Gb in Disk Size
11. Click "Pre-Allocate Full Size"
12. Click Next
13. Click Finish
14. Time to install the operating system (Click "Start" on your Virtualbox interface)
15. Select "Install" and then follow the on-screen instructions
16. Set the hostname as your login followed by 42 (i.e.: user42) (This is the name of your device on the local network)
18. Skip domain name configuration
19. Set a password for root
20. Make a user with your login and set a password for this account
21. Select "Guided - use entire disk and set up encrypted LVM" [Option 03]
22. Select "Separate /home, /var and /tmp partitions" (This setup is crucial for completing the bonus part of born2beroot) [Option 03]
23. Click Yes and wait
24. Adjust the volume group size in guided partitioning to carve out space for a couple more logical volumes
25. Head over to "Configure the Logical Volume Manager" (on the top, 3rd option)
26. Click Yes
27. Click on "Create Logical Volume" (to create two logical volumes named: srv and var-log)
28. Type "srv" as name
29. Repeat step 27
30. Type "var-log"
31. Set them both as "Ext4 journaling file system" and mount them respectively to /srv and /var/log (mine was set already)
32. Avoid scanning for extra installation media.
33. Select the default Debian archive mirror
34. Leave the proxy settings blank
35. Choose not to participate in the package usage survey
36. When it comes to software selection, only select "SSH server" and "standard system utilities" (use space to select it)
37. Ensure to install the GRUB loader (click yes) 
38. Then click on 2nd option (dev/sda)
39. It's time to set up SSH
40. Log in as root and check the SSH service status: systemctl status ssh
41. The output should show that the SSH service is active and running on the default port 22
42. 



Also watch: https://www.youtube.com/watch?v=OQEdjt38ZJA&list=PLHubc7VgWonRLAYVjKUTCzrfbYXHObG0q
Step-by-step Guide Credits: https://github.com/chlimous/42-born2beroot_guide
