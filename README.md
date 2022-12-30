# Computer Networks Assignments
#### Reference material 
- Computer Networking: A Top Down Approach Featuring the Internet, Third Edition, J. Kurose and Keith Ross, Addison-Wesley, 2004
- Computer Networks - A Systems Approach, Fourth Edition, by Larry L. Peterson and Bruce S. Davie, Morgan Kaufmann, 2003
- Computer Networks, Fourth Edition, by Andrew S. Tanenabum, Printice Hall, 2003

## Assignment 1
### Problem 1
#### a) What are the types of computing devices?
<!-- this is Eng. Ahmad's answer-->
Computing devices are separated into desktop computers, mobile devices such as phones and laptops, IoT devices, data centers and supercomputers.

#### b) What is the difference between a distributed system and a network? How are they related?
   - A network is a collection of computer nodes connected together.
   - A distributed system is a collection of computing nodes that's interconnected and appears to the user as a single monolithic system.
   - They're related in the sense that every distributed system is a network with special abstracting software on it.

#### c) Describe transmission type in networks.
- Broadcast:
   - single channel, shared by all nodes
   - data is sent as packets
   - supports single recipient, multicast and broadcast
   - intended recipients are indicated in the packet's address field
- Point-to-point:
   - connection between individual node pairs
   - a packet might go through intermediate nodes before reaching destination
   - there could be multiple routes for a single packet

#### d) What is the purpose of protocols, and what are the general functions they perform?
Protocols ensure successful communication by defining the format and the order of messages, as well as the actions taken on message transmission or receipt.

#### e) What si the difference between circuit switching and packet switching?
- Circuit switching:
   - dedicated lines between nodes
   - data is sent as a continuous stream
   - data is sent at a constant rate
- Packet switching:
   - different nodes use the same lines
   - data is transferred in small messages called packets
   - data is sent at a variable rate

Packet switching allows for more efficient use of communication lines.

### Problem 2
#### a) Describe the layering architecture used to build networks; what is its advantage?
Layered network models separate the process of of communication into a set of small discrete tasks, each assigned to a particular layer that works to perform that task only where:
- each layer performs a single well-defined function
- each layer provides the services of its function to the next layer in the hierarchy
- the chosen layer boundaries result in minimal information flow between layers
- the number of layers is large enough to avoid assigning separate functionalities to one layer, and small enough that minimal message passing occurs so the architecture stays simple and easy to manage.

The layered architecture is an abstraction of the network that helps us understand the network and its components, making it easier to understand the network, manage it and make changes to it.

### b) Explain the relationship and communication between (1.) layers at the same node. (2.) layers at two different nodes.
1. layers at the same node communicate through interfaces.
1. layers at different nodes communicate through protocols.

#### c) What are the main functions of the physical layer?
It transmits raw bits over the communication channel, manages connection initiation and termination, and defines the electrical specifications of the physical medium.

#### ~~d) Suppose that node A wants to send data to node B. Outline how encapsulation is done as the data is moved between different layers at nodes A and B~~

### Problem 3
#### a) Where is the data link layer implemented?
In the network interface card (NIC).

#### ~~b) Draw a block diagram to show the relationship of a network adapter to other host components and the protocol stack functionality.~~

#### c) (1.) Why is flow control needed in the DLL? (2.) Describe two types of control flow.
1. It's needed to avoid overwhelming one of the communicating nodes with data, especially if they're operating at different speeds.
1. - Feedback based: the receiver sends back info that lets the transmitter send more or less data.
   - Rate based: a built-in mechanism at the transmitter limits its transmission rate.

#### d) What is the difference between error detection and error correction? Explain when each strategy should be used.
- Error detection: mechanisms for a receiver node to detect errors.
- Error correction: mechanisms for a receiver node to detect errors and determine their locations so they can be corrected.

### ~~Problem 4~~
### ~~Problem 5~~

## Assignment 2
### ~~Problem 1~~
### ~~Problem 2~~
### ~~Problem 3~~
### Problem 4
#### a) What are the advantages and disadvantages of: (1.) polling protocols (2.) token protocols?
1. Polling protocols:
   - advantages:
      - simple
      - has no chance of collisions
      - easy to implement
   - disadvantages:
      - inefficient and slow
      - requires a central controller which is a single point of failure
2. Token passing protocols:
   - advantages:
      - faster than polling
      - decentralized and more robust than polling
      - results in lower latency
   - disadvantages:
      - has a single point of failure, where if the node holding the token fails, the whole ring fails.
  
#### b) (1.) Explain the Slotted-Aloha protocol. ~~(2.) If there are 4 nodes willing to transmit their frames, draw a sketch that illustrates the disadvantages of Slotted-Aloha.~~
It's a data link layer protocol for frame transmission where:
   - frames are split into slots smaller than teh frame size
   - all the nodes attempt to transmit data at the beginning of a slot
   - if a collision is detected, all the colliding nodes wait a random period of time then attempt to transmit again

### ~~Problem 5~~

## Assignment 3
### Problem 1
#### a) Describe the connection and operation of a switch.
Switches are high performance multi-interface bridges.
   - They are layer 2 devices that connect multiple LANs/network segments with different technologies together.
   - Each LAN segment on a switch port is a separate collision domain.
   - There's no limit on how big a network segment can be.
   - Many switches operate in full-duplex mode, sending and receiving data at the same time.

#### b) What is the difference between a LAN and a subnet?
LANs are physical IP networks separated by routers, while subnets are logical IP networks separated in software ans can either be a superset of multiple LANs or a subset of on LAN.

#### c) What is the LAN (MAC) address?
They're 6 byte _data link layer_ addresses that are unique and permanent to each interface on a NIC, and are used as to identify devices in a network in order to allow routing in local network segments. They are managed and allocated by IEEE and are burned into the ROMs of each NIC.

#### d) What's the function of the ARP protocol?
It's a protocol that translates between IP Addresses and MAC Addresses on local networks.

#### e) What is the ARP table? And what entries does it have?
It's a table that maps IP addresses to MAC addresses, and is stored in the ARP module of every node in a LAN. 
It contains entries for:
   - IP addresses of each node in the LAN
   - MAC addresses of each node in the LAN
   - Time To Live (TTL) for each entry

### Problem 2
#### a) WHat is the advantage of adding collision detection to CSMA?
It helps efficiency and performance by aborting the transmission of corrupted, useless frames.

#### b) The Ethernet frame starts by an 8-byte preamble: (1.) What is the function of this preamble? (2.) Is the preamble included in the calculation of the frame's CRC? Why or why not?
1. It's used:
   - for clock synchronization between the transmitter and the receiver.
   - as a wake up call to the receiver
2. It's not included in the CRC calculation because it's redundant data, that's not part of the frame's payload and contains no useful information.

#### c) Suppose you want to connect 95 nodes 10Base2 Ethernet. How many repeaters do you need? and why?
Four repeaters, because the max number of nodes supported on each bus is 30, and ceil(95/30) = 3

#### d) Describe the Ethernet service type.
It's a connectionless service that provides best effort delivery of frames, and doesn't guarantee delivery or order of delivery.
   - No ACKs or NACKs are passed by senders or receivers.
   - The receiver just discards frames with failed CRC checks.
   - It's blind to the data it transmits:
      - It doesn't detect gaps in the data
      - Or recognize retransmissions
#### e) Why does Ethernet use Manchester encoding? ~~If the bit stream is [11000110], draw a sketch to show how this stream is encoded.~~
It ensures that sender and receiver clocks stay in sync.

### Problem 3
#### a) What is the difference between an infrastructure network and an ad-hoc network?
- Infrastructure networks are 802.11 networks where all devices connect to each other (and maybe the internet) through a single access point
- Ad-hoc networks are a group of 802.11 stations that group themselves together to form a network  with no central control or connections to other networks.

#### b) Explain how the 802.11 media access protocol can reserve access to a channel, and draw a schematic diagram to show the steps used to transmit data.

