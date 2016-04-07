---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: ''
datePublished: '2016-04-07T14:24:30.187Z'
dateModified: '2016-04-07T14:24:29.775Z'
title: Interview Study Guide - Part 5
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-04-07-interview-study-guide-part-5.md
published: true
url: interview-study-guide-part-5/index.html
_type: Article

---
## 5\. RAID

**Understanding RAID levels is important to understanding how our systems work.**

### What is RAID 0? 1, 5, 6, 10?

Specificially, 0 (stripe), 1 (mirror), 4 (dedicated parity), 5 (distributed parity), 6 (same as 5 except has an additional disk and a second distrubuted parity), 10 (both 1 and 0)

There are 3 different types of striping: bit, byte, block

**BACKGROUND INFORMATION/FURTHER STUDY**

### What are raid levels?

The standard RAID levels are a basic set of RAID configurations that employ the techniques of striping, mirroring, or parity to create large reliable data stores from general purpose computer hard disk drives. The most common types today are RAID 0 (striping), RAID 1 and variants (mirroring), RAID 5 (distributed parity) and RAID 6 (dual parity).

**BACKGROUND INFORMATION/FURTHER STUDY**

### How do the various RAID levels work?

**RAID 0:**is a striping type, this takes information being written and splits it on to two different hard drives. Making your write speed much faster. But offers no redundancy if you lose a drive you lose all the data.

**RAID 1:**this takes two hard drives like two 500GB which would 1TB in space but on a raid 1 it mirrors the data on the two hard drives so if one goes down. The data can be restored.

**(Not needed to know but, fun) Raid 2:**In the case of RAID 2 all data are stripped (to the bit levels -- not block). Each bit is written on a different drive/stripe. Such a solution requires the use of Hamming code for error correction. While RAID 2 is being used it is important to synchronize all disks. Such a solution requires that the controller, which makes disks, will spin at the same angular orientation -- in other way the index will not be reached at the same time. Disintegration will lead to total uselessness of drives in array. Such a requirement is not the only drawback. Also the need for long Hamming code generation may prove to be problematic by slowing the whole system down.

**(Not needed but, fun)RAID 3:**works as RAID 0 does -- it uses byte-level stripping -- but it also uses an additional disk in the array. It is used to store checksums and it supports a special processor in parity codes calculating -- so we may call it "the parity disk". The read speed is more than satisfactory but write speed is on the contrary -- the reason being the necessity of checksums calculating (even RAID hardware controllers cannot solve this problem). She second disadvantage is a matter of disk failure. When it happens, the whole system will work much slower. What is more, although RAID 3 is resistant to breakdown (in case of failure of one disk in the array), replacing a damaged disk is very costly. A third problem is the disk used for calculating checksums -- it is usually the bottleneck in the performance of the entire array.

**RAID 4:**is very similar to RAID 3, the main difference is the way of sharing data. They are divided in to blocks (16, 32, 64 lub 128 kB) and written on disk s -- similar to RAID 0\. For each row of written data, any recorded block is written on a parity disk. In short this means that RAID 4 does not strip data at block levels but it uses byte levels for striping (block-level striping with a dedicated parity disk). There are also similarities in relation to RAID 5, but it confines all parity data to a single drive. RAID 4 does not use distributed parity.RAID 4 requires at least three disks for complete implementation and configuration. What is more, it also needs hardware support for parity calculations. This makes it possible to recover data by the appropriate mathematical operations.

**RAID 5:**is one of the most popular implementations. It works almost the same as RAID 4 but with one difference. The parity bits are not recorded on a specifically prepared disk -- they are dispersed throughout the matrix structure. What does this mean in the case of failure? Well, it is much easier to recover data (in case of failure of one disk). Also, the read speed is much higher (in comparison to RAID 0) however, as usually happens, there are also some drawbacks. The necessity of calculating checksums causes a lower write speed. RAID 5 is also expensive in the case of the array reconstruction -- if one of the disks have to be replaced after failure. Also read and write operations will slowdown in such case due to the need of calculating checksums. RAID 5 is the best solution when we talk about data safety. In the case of failure the system will automatically rebuild the lost data so that they can be read (however, the current performance of the matrix will be reduced).

**RAID 6:**is sometimes called RAID 5+1, it is because its mechanism is based on RAID 5\. Generally it is RAID 5 but array enriched with one additional disk. Thus it contains two independent checksums. It is more reliable, but its implementation is more expensive. RAID 6 is resistant so much so that its work will be impossible only after the failure of at least three disks. What does it mean? One important thing: It is two times more resistant than RAID 5\. What is more, the speed of the whole system is higher than in the case of a single disk. It makes RAID 6 an almost ideal solution (if we do not take into account the costs of implementation).

**RAID 10:**is also known as Raid 1 + 0, this would have a striped mirroring of the data being written to the hard drives.

**RAID 0+1:**???

**BACKGROUND INFORMATION/FURTHER STUDY**

Add the minimum number of drives required, for each RAID level above. For example, RAID-1 requires a minimum of 2 drives.

### What is parity and how does it work?

Parity is an error protection scheme. The use of a parity bit is a way of adding checksums into data that can enable the target device to determine whether the data has been received correctly. Using a parity bit is a simple way of checking for errors. Basically, a single data bit is added to the end of a data block to ensure the number of bits in the message is either odd or even. For example, if an even parity is used, the receiving device will know that every correct message must contain an even number of bits; otherwise, there has been an error and the source device must resend. In practice, RAID devices use enhanced forms of parity checking such as vertical and horizontal parity.

**BACKGROUND INFORMATION/FURTHER STUDY**

### Logically, why would you use some over others?

If you are going to be doing large data storage and you need this backups run quickly and kept safely generally you would want to use a parity type setup. If they are simpler details RAID 1 + 0 could work fine.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What RAID level do we most commonly use here?

RAID 5

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is mdraid?

Allows you to create a raid from command line.

**BACKGROUND INFORMATION/FURTHER STUDY**

### Why would it be important to know how Linux RAID works?

???