---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: I would like any candidate to be able to tell me what the typical file permissions mean.
datePublished: '2016-04-07T14:26:58.868Z'
dateModified: '2016-04-07T14:26:58.295Z'
title: Interview Study Guide - Part 2
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-04-07-interview-study-guide-part-2.md
published: true
url: interview-study-guide-part-2/index.html
_type: Article

---
## 2\. File Permissions

**I would like any candidate to be able to tell me what the typical file permissions mean.**

### What is SUID (_set user ID_)?

This is set user id it allows a user to run executable files with elevated privileges this is usually done with root owned files.

The set user ID (SUID) option is used with executable files, and it tells Linux to run the program with the permissions of whoever owns the file rather than with the permissions of the user who runs the program.

For instance,tracerouteis a program owned by root and requires root privileges to run. How do we allow a cPanel user to runtraceroute?

**BACKGROUND INFORMATION/FURTHER STUDY**

[http://en.wikipedia.org/wiki/Setuid][0]

[http://www.linuxnix.com/2011/12/suid-set-suid-linuxunix.html][1]

### What is SGID (_set group ID_)?

This is to set group based privileges within a process much like the setuid.**Knowing this information is essential when dealing with our systems,**because there are times when a file needs to be executed with setuid/gid permissions. For example, the command traceroute has a setuid in order for it to run it would need the root privilege

**BACKGROUND INFORMATION/FURTHER STUDY**

[http://en.wikipedia.org/wiki/Setuid][0]

[http://www.linuxnix.com/2011/12/sgid-set-sgid-linuxunix.html][2]

### What is a sticky bit?

A sticky bit is a file permission for linux that does not allow other users beside itself and the root user to modify or delete the directory. You can set this by doing chmod 1755 or chmod +t directory.

**BACKGROUND INFORMATION/FURTHER STUDY**

[http://en.wikipedia.org/wiki/Sticky\_bit][3]

[http://en.wikipedia.org/wiki/File\_system\_permissions][4]

[http://www.linuxnix.com/2012/01/sticky-bit-set-linux.html][5]

### What permissions do these additional symbols represent? (_+_(plus),_._(dot),_@_)

+(plus) suffix indicates an access control list that can grant additional permissions. Details are available withman getfacl.

.(dot) suffix indicates an SELinux context is present. Details may be listed with the commandls

-Z

. (Extra files removed from output to increase ease of identification and patterns.)

@suffix indicates extended file attributes (see link below) are present.

**BACKGROUND INFORMATION/FURTHER STUDY**

[http://en.wikipedia.org/wiki/File\_system\_permissions][4]

For extended file attributes using the@symbol:

[http://en.wikipedia.org/wiki/Extended\_file\_attributes][6](read Intro, Linux and OS X sections)

### When and why would you use these?

**setuid:**if you wanted to give access to running a script or binary file that is owned to root. Setting up a setuid will allow a user with the right permissions to run that script/binary file.

**setgid:**would allow a certain group with the correct permissions to run a list of files and modify them, or could be even set to a directory.

**sticky bit:**???

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is umask and how does it work?

**UMASK (User Mask or User file creation MASK)**is the default permission or base permissions given when a new file (even folder too, as Linux treats everything as files) is created on a Linux machine. Most of the Linux distros give 022 (0022) as default UMASK. In other words, it is a system level default for permissions for newly created files/directories in the machine.

The mask is stored as a groups of bits. It may be displayed in octal (e.g., 0754), or symbolic notation (e.g., u=rwx,g=rx,o=r) (see symbolic notation below for details).**The umask command uses the same octal and symbolic notation as the chmod command.**

#### How to calculate umask in Linux

The umask will be the same for files and directories. For example, the umask 0022 above, will be applied to both files and directories with no change in itself. However, maximum file permissions and maximum directory permissions are different.

**The minimum UMASK value for a directory is 000; the maximum is 777\.**

**The minimum UMASK value for a file is 000; the maximum is 666\.**

The actual calculation is performed using this formula:

> maximum permissions value - umask value = default permissions

For you mathematicians who love numbers:

#### Why is 666 the maximum value for a file?

Only scripts and binaries should have execute permissions. Normal, and regular, files should only have read and write permissions. Directories require execute permissions for viewing the contents in it, so they need to have 777 available to them.

Below are the various values and permissions used for umask. You will observe these are inverse to the permission values used when setting permissions to files and directories with thechmodcommand.

**BACKGROUND INFORMATION/FURTHER STUDY**

[http://en.wikipedia.org/wiki/Umask][7]

[http://www.linuxnix.com/2011/12/umask-define-linuxunix.html][8]

[http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html][9]

[http://askubuntu.com/questions/44542/what-is-umask-and-how-does-it-work][10]

[http://unixhelp.ed.ac.uk/examples/umask.html][11]

[0]: https://web.archive.org/web/20150320020135/http://en.wikipedia.org/wiki/Setuid
[1]: https://web.archive.org/web/20150320020135/http://www.linuxnix.com/2011/12/suid-set-suid-linuxunix.html
[2]: https://web.archive.org/web/20150320020135/http://www.linuxnix.com/2011/12/sgid-set-sgid-linuxunix.html
[3]: https://web.archive.org/web/20150320020135/http://en.wikipedia.org/wiki/Sticky_bit
[4]: https://web.archive.org/web/20150320020135/http://en.wikipedia.org/wiki/File_system_permissions
[5]: https://web.archive.org/web/20150320020135/http://www.linuxnix.com/2012/01/sticky-bit-set-linux.html
[6]: https://web.archive.org/web/20150320020135/http://en.wikipedia.org/wiki/Extended_file_attributes
[7]: https://web.archive.org/web/20150320020135/http://en.wikipedia.org/wiki/Umask
[8]: https://web.archive.org/web/20150320020135/http://www.linuxnix.com/2011/12/umask-define-linuxunix.html
[9]: https://web.archive.org/web/20150320020135/http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html
[10]: https://web.archive.org/web/20150320020135/http://askubuntu.com/questions/44542/what-is-umask-and-how-does-it-work
[11]: https://web.archive.org/web/20150320020135/http://unixhelp.ed.ac.uk/examples/umask.html