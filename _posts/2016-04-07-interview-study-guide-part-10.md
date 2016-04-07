---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: ''
datePublished: '2016-04-07T14:19:17.076Z'
dateModified: '2016-04-07T14:18:12.037Z'
title: Interview Study Guide - Part 10
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-04-07-interview-study-guide-part-10.md
published: true
url: interview-study-guide-part-10/index.html
_type: Article

---
## 10\. Linux Kernel

### What is the Linux Kernel?

The central module of an operating system. It is the part of the operating system that loads first, and it remains in main memory. Because it stays in memory, it is important for the kernel to be as small as possible while still providing all the essential services required by other parts of the operating system and applications. Typically, the kernel is responsible for memory management, process and task management, and disk management.

There is a modular and gigantic kernels. Modular only loads configured modules where as gigantic loads all of the modules.

**BACKGROUND INFORMATION/FURTHER STUDY**

### On a general basis, what are it's primary functions?

A kernel connects the application software to the hardware of a computer.

[http://en.wikipedia.org/wiki/Kernel\_%28computing%29][0]

t the top is the user, or application, space. This is where the user applications are executed. Below the user space is the kernel space. Here, the Linux kernel exists. There is also the GNU C Library (glibc). This provides the system call interface that connects to the kernel and provides the mechanism to transition between the user-space application and the kernel. This is important because the kernel and user application occupy different protected address spaces. And while each user-space process occupies its own virtual address space, the kernel occupies a single address space.

The Linux kernel can be further divided into three gross levels. At the top is the system call interface, which implements the basic functions such as read and write. Below the system call interface is the kernel code, which can be more accurately defined as the architecture-independent kernel code. This code is common to all of the processor architectures supported by Linux. Below this is the architecture-dependent code, which forms what is more commonly called a BSP (Board Support Package). This code serves as the processor and platform-specific code for the given architecture.

#### System call interface

The SCI is a thin layer that provides the means to perform function calls from user space into the kernel. As discussed previously, this interface can be architecture dependent, even within the same processor family. The SCI is actually an interesting function-call multiplexing and demultiplexing service. You can find the SCI implementation in ./linux/kernel, as well as architecture-dependent portions in ./linux/arch.

#### Process management

##### What is a kernel?

As shown in Figure 3, a kernel is really nothing more than a resource manager. Whether the resource being managed is a process, memory, or hardware device, the kernel manages and arbitrates access to the resource between multiple competing users (both in the kernel and in user space).

Process management is focused on the execution of processes. In the kernel, these are called threads and represent an individual virtualization of the processor (thread code, data, stack, and CPU registers). In user space, the term process is typically used, though the Linux implementation does not separate the two concepts (processes and threads). The kernel provides an application program interface (API) through the SCI to create a new process (fork, exec, or Portable Operating System Interface \[POSIX\] functions), stop a process (kill, exit), and communicate and synchronize between them (signal, or POSIX mechanisms).

Also in process management is the need to share the CPU between the active threads. The kernel implements a novel scheduling algorithm that operates in constant time, regardless of the number of threads vying for the CPU. This is called the O(1) scheduler, denoting that the same amount of time is taken to schedule one thread as it is to schedule many. The O(1) scheduler also supports multiple processors (called Symmetric MultiProcessing, or SMP). You can find the process management sources in ./linux/kernel and architecture-dependent sources in ./linux/arch.

#### Memory management

Another important resource that's managed by the kernel is memory. For efficiency, given the way that the hardware manages virtual memory, memory is managed in what are called pages (4KB in size for most architectures). Linux includes the means to manage the available memory, as well as the hardware mechanisms for physical and virtual mappings.

But memory management is much more than managing 4KB buffers. Linux provides abstractions over 4KB buffers, such as the slab allocator. This memory management scheme uses 4KB buffers as its base, but then allocates structures from within, keeping track of which pages are full, partially used, and empty. This allows the scheme to dynamically grow and shrink based on the needs of the greater system.

Supporting multiple users of memory, there are times when the available memory can be exhausted. For this reason, pages can be moved out of memory and onto the disk. This process is called swapping because the pages are swapped from memory onto the hard disk. You can find the memory management sources in ./linux/mm.

#### Virtual file system

The virtual file system (VFS) is an interesting aspect of the Linux kernel because it provides a common interface abstraction for file systems. The VFS provides a switching layer between the SCI and the file systems supported by the kernel.

At the top of the VFS is a common API abstraction of functions such as open, close, read, and write. At the bottom of the VFS are the file system abstractions that define how the upper-layer functions are implemented. These are plug-ins for the given file system (of which over 50 exist). You can find the file system sources in ./linux/fs.

Below the file system layer is the buffer cache, which provides a common set of functions to the file system layer (independent of any particular file system). This caching layer optimizes access to the physical devices by keeping data around for a short time (or speculatively read ahead so that the data is available when needed). Below the buffer cache are the device drivers, which implement the interface for the particular physical device.

#### Network stack

The network stack, by design, follows a layered architecture modeled after the protocols themselves. Recall that the Internet Protocol (IP) is the core network layer protocol that sits below the transport protocol (most commonly the Transmission Control Protocol, or TCP). Above TCP is the sockets layer, which is invoked through the SCI.

The sockets layer is the standard API to the networking subsystem and provides a user interface to a variety of networking protocols. From raw frame access to IP protocol data units (PDUs) and up to TCP and the User Datagram Protocol (UDP), the sockets layer provides a standardized way to manage connections and move data between endpoints. You can find the networking sources in the kernel at ./linux/net.

#### Device drivers

The vast majority of the source code in the Linux kernel exists in device drivers that make a particular hardware device usable. The Linux source tree provides a drivers subdirectory that is further divided by the various devices that are supported, such as Bluetooth, I2C, serial, and so on. You can find the device driver sources in ./linux/drivers.

Architecture-dependent code

While much of Linux is independent of the architecture on which it runs, there are elements that must consider the architecture for normal operation and for efficiency. The ./linux/arch subdirectory defines the architecture-dependent portion of the kernel source contained in a number of subdirectories that are specific to the architecture (collectively forming the BSP). For a typical desktop, the i386 directory is used. Each architecture subdirectory contains a number of other subdirectories that focus on a particular aspect of the kernel, such as boot, kernel, memory management, and others. You can find the architecture-dependent code in ./linux/arch

**BACKGROUND INFORMATION/FURTHER STUDY**

### On lower levels, how does the CPU scheduler work?

???

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is I/O?

I/O (input/output), pronounced "eye-oh," describes any operation, program, or device that transfers data to or from a computer. Typical I/O devices are printers, hard disks, keyboards, and mouses. In fact, some devices are basically input-only devices (keyboards and mouses); others are primarily output-only devices (printers); and others provide both input and output of data (hard disks, diskettes, writable CD-ROMs).

**BACKGROUND INFORMATION/FURTHER STUDY**

### What different IO schedulers are available?

CFQ:

NOOP:

Deadlines:

Anticipatory Scheduling:

[http://en.wikipedia.org/wiki/Anticipatory\_scheduling][1]

[http://en.wikipedia.org/wiki/CFQ][2]

[http://en.wikipedia.org/wiki/Deadline\_scheduler][3]

[http://en.wikipedia.org/wiki/Noop\_scheduler][4]

### What different IO schedulers are available?

* CFQ:
* NOOP:
* Deadlines:
* Anticipatory Scheduling:

**BACKGROUND INFORMATION/FURTHER STUDY**

[http://en.wikipedia.org/wiki/Anticipatory\_scheduling][1]

[http://en.wikipedia.org/wiki/CFQ][2]

[http://en.wikipedia.org/wiki/Deadline\_scheduler][3]

[http://en.wikipedia.org/wiki/Noop\_scheduler][4]

### What are the differences between each of them?

**CFQ:**places synchronous requests submitted by processes into a number of per-process queues and then allocates time slices for each of the queues to access the disk. The length of the time slice and the number of requests a queue is allowed to submit depends on the I/O priority of the given process. Asynchronous requests for all processes are batched together in fewer queues, one per priority. While CFQ does not do explicit anticipatory I/O scheduling, it achieves the same effect of having good aggregate throughput for the system as a whole, by allowing a process queue to idle at the end of synchronous I/O thereby "anticipating" further close I/O from that process. It can be considered a natural extension of granting I/O time slices to a process.

**Anticipatory Scheduling:**is for scheduling hard disks input/output. It tries to seek efficiency of the disk utilization by "Anticipating" Synchronous Read Operations. "Deceptive idleness" is a situation where a process appears to be finished reading from the disk when it is actually processing data in preparation of the next read operation. This will cause a normal work-conserving I/O scheduler to switch to servicing I/O from an unrelated process. This situation is detrimental to the throughput of synchronous reads, as it degenerates into a seeking workload.\[1\] Anticipatory scheduling overcomes deceptive idleness by pausing for a short time (a few milliseconds) after a read operation in anticipation of another close-by read requests.\[2\]

Anticipatory scheduling yields significant improvements in disk utilization for some workloads.\[3\] In some situations the Apache web server may achieve up to 71% more throughput from using anticipatory scheduling.\[4\]

**NOOP:**The NOOP scheduler inserts all incoming I/O requests into a simple FIFO queue and implements request merging. This scheduler is useful when it has been determined that the host should not attempt to re-order requests based on the sector numbers contained therein. In other words, the scheduler assumes that the host is definitionally unaware of how to productively re-order requests.

There are (generally) three basic situations where this situation is desirable:

If I/O scheduling will be handled at a lower layer of the I/O stack. For example: at the block device, by an intelligent RAID controller, Network Attached Storage, or by an externally attached controller such as a storage subsystem accessed through a switched Storage Area Network)\[1\] Since I/O requests are potentially re-scheduled at the lower level, resequencing IOPs at the host level can create a situation where CPU time on the host is being spent on operations that will just be undone when they reach the lower level, increasing latency/decreasing throughput for no productive reason.

Because accurate details of sector position are hidden from the host system. An example would be a RAID controller that performs no scheduling on its own. Even though the host has the ability to re-order requests and the RAID controller does not, the host systems lacks the visibility to accurately re-order the requests to lower seek time. Since the host has no way of knowing what a more streamlined queue would "look" like, it can not restructure the active queue in its image, but merely pass them onto the device that is (theoretically) more aware of such details.

Because movement of the read/write head has been determined to not impact application performance in a way that justifies the additional CPU time being spent re-ordering requests. This is usually the case with non-rotational media such as flash drives or Solid-state drives. This is not to say NOOP is necessarily the preferred I/O scheduler for the above scenarios. As with any performance tuning, all guidance will be based on observed work load patterns (undermining one's ability to create simplistic rules of thumb). If there is contention for available I/O bandwidth from other applications, it is still possible that other schedulers will generate better performance by virtue of more intelligently carving up that bandwidth for the applications deemed most important. For example, with a LDAP directory server a user may want deadline's read preference and latency guarantees. In another example, a user with a desktop system running many different applications may want to have access to CFQ's tunables or its ability to prioritize bandwidth for particular applications over others (ionice).

It should be noted that without contention between applications there is little to no benefit to selecting a scheduler for the listed three scenarios. This is due to a resulting inability to deprioritize one workload's operations in a way that makes additional capacity available to another workload. If the I/O paths are not saturated and the requests for all the workloads fail to cause an unreasonable shifting around of drive heads (that the OS is aware of) the benefit of prioritizing one workload may create a situation where CPU time spent scheduling I/O is wasted in excess to the benefit of doing such.

The NOOP scheduler is the simplest I/O scheduler for the Linux kernel. This scheduler was developed by Jens Axboe.

The NOOP scheduler inserts all incoming I/O requests into a simple, unordered FIFO queue and implements request merging.

The scheduler assumes I/O performance optimization will be handled at some other layer of the I/O hierarchy; e.g., at the block device; by an intelligent HBA such as a Serial Attached SCSI (SAS) RAID controller or by an externally attached controller such as a storage subsystem accessed through a switched Storage Area Network).

NOOP scheduler is best used with solid state devices such as flash memory or in general with devices that do not depend on mechanical movement to access data (meaning typical "hard disk" drive technology consisting of seek time primarily, plus rotational latency). Such non-mechanical devices do not require re-ordering of multiple I/O requests, a technique that groups together I/O requests that are physically close together on the disk, thereby reducing average seek time and the variability of I/O service time.

**Deadline Scheduler:**The main goal of the Deadline scheduler is to guarantee a start service time for a request. It does that by imposing a deadline on all I/O operations to prevent starvation of requests. It also maintains two deadline queues, in addition to the sorted queues (both read and write). Deadline queues are basically sorted by their deadline (the expiration time), while the sorted queues are sorted by the sector number.

Before serving the next request, the Deadline scheduler decides which queue to use. Read queues are given a higher priority, because processes usually block on read operations. Next, the Deadline scheduler checks if the first request in the deadline queue has expired. Otherwise, the scheduler serves a batch of requests from the sorted queue. In both cases, the scheduler also serves a batch of requests following the chosen request in the sorted queue. By default, read requests have an expiration time of 500 ms, write requests expire in 5 seconds.

**noop**is just a First In First Out standard queue of I/O operations. A trivial scheduler that just passes down the I/O that comes to it. Useful for checking whether complex I/O scheduling decisions of other schedulers are not causing I/O performance regressions.

In some cases it can be helpful for devices that do I/O scheduling themselves, as intelligent storage, or devices that do not depend on mechanical movement, like SSDs. Usually, the DEADLINE I/O scheduler is a better choice for these devices, but due to less overhead NOOP may produce better performance on certain workloads.

**cfq (Completely Fair Scheduling)**is similar to the Round Robin algorithm and basically allots a fixed execution time for each I/O operation (they are implemented as a circular queue) CFQ is a fairness-oriented scheduler and is used by default on SUSE Linux Enterprise Server. The algorithm assigns each thread a time slice in which it is allowed to submit I/O to disk. This way each thread gets a fair share of I/O throughput. It also allows assigning tasks I/O priorities which are taken into account during scheduling decisions (see man 1 ionice). The CFQ scheduler has the following tunable parameters:

**deadline**is like a priority queue with an aging concept. Basically it adds a dealine for each I/O operation & implements a priority queue

DEADLINE is a latency-oriented I/O scheduler. Each I/O request has got a deadline assigned. Usually, requests are stored in queues (read and write) sorted by sector numbers. The DEADLINE algorithm maintains two additional queues (read and write) where the requests are sorted by deadline. As long as no request has timed out, the "sector" queue is used. If timeouts occur, requests from the "deadline" queue are served until there are no more expired requests. Generally, the algorithm prefers reads over writes.

This scheduler can provide a superior throughput over the CFQ I/O scheduler in cases where several threads read and write and fairness is not an issue. For example, for several parallel readers from a SAN and for databases (especially when using "TCQ" disks). The DEADLINE scheduler has the following tunable parameters:

**the Anticipatory scheduler**introduces a controlled delay before dispatching the I/O to attempt to aggregate and/or re-order requests improving locality and reducing disk seek operations. This algorithm is intended to optimize systems with small or slow disk subsystems;

**the Completely Fair Queuing (CFQ)**scheduler maintains a scalable per-process I/O queue and attempts to distribute the available I/O bandwidth equally among all I/O requests;

**the Deadline scheduler**uses a deadline algorithm to minimize I/O latency for a given I/O request;

**the Noop scheduler**is a simple**FIFO**queue, and it assumes performance of the I/O has been or will be optimized at the block device.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is a fork?

fork() creates a child process that differs from the parent process only in its PID and PPID, and in the fact that resource utilizations are set to 0\. File locks and pending signals are not inherited.

Under Linux, fork() is implemented using copy-on-write pages, so the only penalty that it incurs is the time and memory required to duplicate the parent's page tables, and to create a unique task structure for the child.

**BACKGROUND INFORMATION/FURTHER STUDY**

### Missing question here?

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is a System Call?

In computing, a system call is how a program requests a service from an operating system's kernel. This may include hardware related services (e.g. accessing the hard disk), creating and executing new processes, and communicating with integral kernel services (like scheduling). System calls provide an essential interface between a process and the operating system.

[0]: https://web.archive.org/web/20150320081212/http://en.wikipedia.org/wiki/Kernel_%28computing%29
[1]: https://web.archive.org/web/20150320081212/http://en.wikipedia.org/wiki/Anticipatory_scheduling
[2]: https://web.archive.org/web/20150320081212/http://en.wikipedia.org/wiki/CFQ
[3]: https://web.archive.org/web/20150320081212/http://en.wikipedia.org/wiki/Deadline_scheduler
[4]: https://web.archive.org/web/20150320081212/http://en.wikipedia.org/wiki/Noop_scheduler