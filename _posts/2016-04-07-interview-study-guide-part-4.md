---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: 'Having a basic understanding of networking fundamentals gives candidates the basis for expanding their knowledge into other, more advanced, areas; as they work on normal duties, for this position, and once they become an Admin.'
datePublished: '2016-04-07T14:25:38.496Z'
dateModified: '2016-04-07T14:25:37.665Z'
title: Interview Study Guide - Part 4
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-04-07-interview-study-guide-part-4.md
published: true
url: interview-study-guide-part-4/index.html
_type: Article

---
## 4\. Basic Understanding of Network Concepts

**Having a basic understanding of networking fundamentals gives candidates the basis for expanding their knowledge into other, more advanced, areas; as they work on normal duties, for this position, and once they become an Admin.**

### I typically like people to know how to subnet.

Number of available hosts:

(2^n)-2

**BACKGROUND INFORMATION/FURTHER STUDY**

[http://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13790-8.html][0]

[http://www.techrepublic.com/article/ip-subnetting-made-easy/][1]

### Additionally, I like candidates to have a slightly more in-depth knowledge of different protocols.

**TCP:**Transmission Control Protocol

**UDP:**User Datagram Protocol

**HTTP:**Hyper Text Transfer Protocol

**FTP:**File Transfer Protocol

**SMTP:**Simple Mail Transfer Protocol

**TELNET:**

**ICMP:**Internet Control Message Protocol

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is the difference between UDP and TCP? (there is a lot)

**TCP:**is connection-oriented protocol. When a file or message send it will get delivered unless connections fails. If connection lost, the server will request the lost part. There is no corruption while transferring a message. If you send two messages along a connection, one after the other, you know the first message will get there first. You don't have to worry about data arriving in the wrong order. When the low level parts of the TCP "stream" arrive in the wrong order, resend requests have to be sent, and all the out of sequence parts have to be put back together, so requires a bit of work to piece together. Data is read as a "stream," with nothing distinguishing where one packet ends and another begins. There may be multiple packets per read call. World Wide Web (Apache TCP port 80), e-mail (SMTP TCP port 25 Postfix MTA), File Transfer Protocol (FTP port 21) and Secure Shell (OpenSSH port 22) etc.

**UDP:**is connectionless protocol. When you a send a data or message, you don't know if it'll get there, it could get lost on the way. There may be corruption while transferring a message. If you send two messages out, you don't know what order they'll arrive in i.e., no ordered, no ordering of messages, no tracking connections, etc. It's just fire and forget! This means it's a lot quicker, and the network card / OS have to do very little work to translate the data back from the packets. Packets are sent individually and are guaranteed to be whole if they arrive. One packet per one read call.Domain Name System (DNS UDP port 53), streaming media applications such as IPTV or movies, Voice over IP (VoIP), Trivial File Transfer Protocol (TFTP) and online multiplayer games, etc.

**BACKGROUND INFORMATION/FURTHER STUDY**

### Why would you use one instead of the other?

**UDP:**Another case is when you are delivering data that can be lost because newer data coming in will replace that previous data/state. Weather data, video streaming, a stock quotation service (not used for actual trading), or gaming data come to mind. One other case is for multicast traffic. UDP can be multicasted to multiple hosts whereas TCP cannot do this at all.

**TCP:**is for reliable transmission of the data if you want to make sure the data gets from point a to point b. TCP is the way to go.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is ICMP?

ICMP is a message control and error-reporting protocol between a host server and a gateway to the Internet. ICMP uses Internet Protocol (IP) datagrams, but the messages are processed by the IP software and are not directly apparent to the application user.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is windowing?

In TCP, after sending a certain amount of data, the sender has to wait for a confirmation, before sending more. The amount of data that can be sent before receiving a confirmation is called the "window size". This window size may vary during the transmission, depending on the quality of the link.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is the format of a TCP header?

TCP Header Format

**Source Port**

Bit-size: 16 bits

The source port number.

**Destination Port**

Bit-size: 16 bits

The destination port number.

**Sequence Number**

Bit-size: 32 bits

The sequence number of the first data octet in this segment (except when SYN is present). If SYN is present the sequence number is the initial sequence number (ISN) and the first data octet is ISN+1\.

**Acknowledgment Number**

Bit-size: 32 bits

If the ACK control bit is set this field contains the value of the next sequence number the sender of the segment is expecting to receive. Once a connection is established this is always sent.

**Data Offset**

Bit-size: 4 bits

The number of 32 bit words in the TCP Header. This indicates where the data begins. The TCP header (even one including options) is an integral number of 32 bits long.

**Reserved**

Bit-size: 6 bits

Reserved for future use. Must be zero.

**Control Bits**

Bit-size: 6 bits (from left to right, one bit each)

URG - Urgent Pointer field significant

ACK - Acknowledgment field significant

PSH - Push Function

RST - Reset the connection

SYN - Synchronize sequence numbers

FIN - No more data from sender

**Window**

Bit-size: 16 bits

The number of data octets beginning with the one indicated in the acknowledgment field which the sender of this segment is willing to accept.

**Checksum**

Bit-size: 16 bits

The checksum field is the 16 bit one's complement of the one's complement sum of all 16 bit words in the header and text. If a segment contains an odd number of header and text octets to be checksummed, the last octet is padded on the right with zeros to form a 16 bit word for checksum purposes. The pad is not transmitted as part of the segment. While computing the checksum, the checksum field itself is replaced with zeros.

The checksum also covers a 96 bit pseudo header conceptually prefixed to the TCP header. This pseudo header contains the Source Address, the Destination Address, the Protocol, and TCP length. This gives the TCP protection against misrouted segments. This information is carried in the Internet Protocol and is transferred across the TCP/Network interface in the arguments or results of calls by the TCP on the IP.

The TCP Length is the TCP header length plus the data length in octets (this is not an explicitly transmitted quantity, but is computed), and it does not count the 12 octets of the pseudo header.

**Urgent Pointer**

Bit-size: 16 bits

This field communicates the current value of the urgent pointer as a positive offset from the sequence number in this segment. The urgent pointer points to the sequence number of the octet following the urgent data. This field is only be interpreted in segments with the URG control bit set.

**Options**

Bit-size: variable

Options may occupy space at the end of the TCP header and are a multiple of 8 bits in length. All options are included in the checksum. An option may begin on any octet boundary. There are two cases for the format of an option:

Case 1: A single octet of option-kind.

Case 2: An octet of option-kind, an octet of option-length, and the actual option-data octets.

The option-length counts the two octets of option-kind and option-length as well as the option-data octets.

Note that the list of options may be shorter than the data offset field might imply. The content of the header beyond the End-of-Option option must be header padding (i.e., zero).

A TCP must implement all options.

Currently defined options include (kind indicated in octal):

**End of Option List**

This option code indicates the end of the option list. This might not coincide with the end of the TCP header according to the Data Offset field. This is used at the end of all options, not the end of each option, and need only be used if the end of the options would not otherwise coincide with the end of the TCP header.

**No-Operation**

This option code may be used between options, for example, to align the beginning of a subsequent option on a word boundary. There is no guarantee that senders will use this option, so receivers must be prepared to process options even if they do not begin on a word boundary.

**Maximum Segment Size**

Maximum Segment Size Option Data: 16 bits

If this option is present, then it communicates the maximum receive segment size at the TCP which sends this segment. This field must only be sent in the initial connection request (i.e., in segments with the SYN control bit set). If this option is not used, any segment size is allowed.

**Padding**

Bit-size: variable

The TCP header padding is used to ensure that the TCP header ends and data begins on a 32 bit boundary. The padding is composed of zeros.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is the format of a UDP header

UDP Header Format

**Source Port**

Bit-size: 16 bits

The source port number fo the process that originated the UDP mesage on the source device. This will normall be an ephemeral (client) port number for a request sent by a client to server, or a well-known/registered (server) port number for a reply sent by a server to a client.

**Destination Port**

Bit-size: 16 bits

The destination port number of the process that is the ultimate intended recipient of the message on the destination device. This will usually be a well-known/registered (server) port number for a client request, or an ephermeral (client) port number for a server reply.

**Length**

Bit-size: 16 bits

The length of the entire UDP datagram, including bothheaderandDatafields.

**Checksum**

Bit-size: 16 bits

An optional checksum computed over the entire UDP datagram plus a special "pseudo header" of fields.

**Data**

Bit-size: variable

The encapsulated higher-layer message to be sent.

**BACKGROUND INFORMATION/FURTHER STUDY**

### Can you read a traceroute?

Yes

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is a Frame?

A frame is a digital data transmission unit that includes frame synchronization, i.e., a sequence of bits or symbols making it possible for the receiver to detect the beginning and end of the packet in the stream of symbols or bits. If a receiver is connected to the system in the middle of a frame transmission, it ignores the data until it detects a new frame synchronization sequence.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is the difference between a hub and a switch?

A hub is something that only allows one device to talk at a time. Where as a switch allows any of the ports to talk and transfer traffic.

A hub broadcasts data on all ports and is not able to tell the difference between what is connected on which port. This can cause a slowdown in network response time. if it has a 10/100 and has multiple devices connected. That is shared across all of the devices slowing down the performance.

Where as a switch is able to differentiate what is connected to each port. It keeps track of what MAC Address is on which port. This way when a frame is send to the switch is knows where to route it and gives full 10/100MB for each of the ports preventing a performance reduction.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is the difference between a switch and a router?

A router sits at the edge of a network, or between two networks. It routes packets or traffic via ports Using headers and forwarding tables, routers determine the best path for forwarding the packets. Router use protocols such as ICMP to communicate with each other and configure the best route between any two hosts.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is the OSI chart? and Understand the OSI chart.

So after the end user is using a computer to interface with networks/internet this how it would follow:

**Layer 7 - Application Layer**

This is the actual program they are interacting with to make a connection to service they are wanting. Ex: Firefox, google chat, Chrome.

**Layer 6 - Presentation Layer**

This is the level of the OS (operating system.) it is the where the encryption/decription happens.

**Layer 5 - Session Layer**

This is the layer that checks and establishes the session between you and the place the data is being sent, (sending an email, connecting to a website) to see if you have the ability to make that connection or if you are being blacklisted.

**Layer 4 - Transport Layer**

This deals with the sending of the data in Packets. This layer will decide if it's going to be breaking up what you are sending into multiple packets or a single packets.

**Layer 3 - Network Layer**

This is the layer where IP addresses reside. This where routers reside as well,

**Layer 2 - Datalink Layer**

This is the layer where MAC addresses reside. This is where Switches reside as well. this is where the data is being passed through to the next system.

**Layer 1 - Physical Layer**

This has to do with all the hardware the physical things you can touch on a network. "cables, computers, switches, routers, hubs."

[0]: https://web.archive.org/web/20150320081217/http://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13790-8.html
[1]: https://web.archive.org/web/20150320081217/http://www.techrepublic.com/article/ip-subnetting-made-easy/