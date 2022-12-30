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

#### d) Suppose that node A wants to send data to node B. Outline how encapsulation is done as the data is moved between different layers at nodes A and B
```
[A]                        [B]
---------------------      --------------------
|  Application  🡫   |     |   🡫  Application  |        
---------------------      --------------------
|  Transport    🡫 🡩 |     | 🡩 🡫  Transport    |      
---------------------      --------------------
|  Network      🡫 🡩 |     | 🡩 🡫  Network      |    
---------------------      --------------------
|  Link         🡫 🡩 |     | 🡩 🡫  Link         | 
---------------------      --------------------
|  Physical       🡩 |<--->| 🡩    Physical     |       
---------------------      --------------------
```

### Problem 3
#### a) Where is the data link layer implemented?
In the network interface card (NIC).

#### b) Draw a block diagram to show the relationship of a network adapter to other host components and the protocol stack functionality.
![](README.d/ass2-prob2-protocol-stack.png)

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
  
#### b) (1.) Explain the Slotted-Aloha protocol. (2.) If there are 4 nodes willing to transmit their frames, draw a sketch that illustrates the disadvantages of Slotted-Aloha.
1. It's a data link layer protocol for frame transmission where:
   - frames are split into slots smaller than teh frame size
   - all the nodes attempt to transmit data at the beginning of a slot
   - if a collision is detected, all the colliding nodes wait a random period of time then attempt to transmit again
1. The notation C, E and S represent a collision, an empty slot and a successful transmission, respectively.
   ![](README.d/ass2-prob4-aloha.png)

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
#### e) (1.) Why does Ethernet use Manchester encoding? (2.) If the bit stream is [11000110], draw a sketch to show how this stream is encoded.
1. It ensures that sender and receiver clocks stay in sync.
1. Baseband: 
![](README.d/ass3-prob2-baseband.png)
Manchester encoding:
![](README.d/ass3-prob2-manchester.png)
### Problem 3
#### a) What is the difference between an infrastructure network and an ad-hoc network?
- Infrastructure networks are 802.11 networks where all devices connect to each other (and maybe the internet) through a single access point
- Ad-hoc networks are a group of 802.11 stations that group themselves together to form a network  with no central control or connections to other networks.

<table border="0"><tr><td>

#### b) Explain how the 802.11 media access protocol can reserve access to a channel, and draw a schematic diagram to show the steps used to transmit data.
It uses RTS and CTS frames where the RTS frame is sent to the receiver and is heard by all devices in its vicinity, and if no collisions or fading occur to it, access to the receive is reserved and it sends back a CTS frame.

#### c) In 802.11 MAP, explain (1.) when DIFS and SIFS are used. (2.) Which one is longer and why?
1. DIFS is used before the very first transmission. SIFS is used after initiation, in connections subsequent to the first.
1. DIFS is longer because:
   - it's used to sense the readiness of a completely opaque station
   - to give higher priority to previously established connections over new attempts.

#### d) Explain how the hidden station problem can be avoided.
RTS frames are sent to be detected in the receivers vicinity, if a hidden station exists collisions will occur with this RTS frame, so no CTS frames will be sent back and no connection will be established.
</td><td>

![rts/cts/difs/sifs -  sequence diagram](README.d/ass3-prob3-seq.png)
</td></tr></table>

### Problem 4
#### a) What are the limitations of using hubs to connect nodes?
- all network segments must use the same ethernet technology
- independent collision domains are combined into one
- total number of hosts and tiers is limited

#### b) What are the types of switches? What is the strategy used to transmit frames by each type?
- Store and Forward: all frames are stored in a buffer until they are completely received, then they are transmitted. If the output buffer is empty but a frame wasn't fully received, a delay is generated by the switch.
- Cut-through switching: frames are transmitted as they come; If the output buffer is empty the switch transmits the start of the frame before receivin its end.
  
#### c) What is the maximum store and forward delay for a switch if the frame length is 900 bytes, the transmission rate of the inbound link is 24\*10^5 bit/sec, and teh transmission rate of outbound link is 36\*10^5 bit/sec?
max delay = (900\*8 bits) / (24\*10^5 bits/sec) = 0.003 sec

### Problem 5
#### ~~a) Assign MAC addresses to the nodes and routers~~
#### ~~b) Give the ARP table for node D, assuming it has recently communicated with all other nodes.~~
#### c) Explain the steps taken when A sends E a frame.
- A send the frame to interface 1 of the router R1
- the router R1 reads the frame's destination IP and checks whether its directly connected to it or not
- R1 finds that the destination node isn't directly connected to it, but is reachable through router R2, so it transmits the frame to R2 through R1 interface 2
- R2 checks the destination IP and finds that the node is in one of its LANs
- R2 forwards the frame to node E through its second interface.

#### d) Explain how a switch table is built.
The switch table is built automatically as follows:
- It's initially empty
- When a frame arrives on one of the interfaces and its destination isn't in the table, the switch forwards copies of the frame on all its interfaces except the one it arrived on.
- for each frame received, the switch stores in its table the source LAN address, the interface on which the frame arrived and the current time.

## Assignment 4
### Problem 1
#### a) How many collision domains are there in the network? List the collision domains and explain your answer.
![](README.d/ass4-prob1-topology.png)

There are 3 collision domains: {r,n}, {s,n}, and {p,q,k,t,u,j,h,n,G}
All devices are in subnetworks of the same router, and are all connected by hubs except for r, and which are connected by a switch; Hubs combine collision domains, and switches keep them separate.

#### b) If host p uses 10BaseT Ethernet, do hosts {q,r,s,t,u} also have to use 10BaseT Ethernet? Explain your answer.
No, only hosts {q,t,u} have to use 10BaseT Ethernet, because nodes {r,s} are separated from p by a switch, which is a layer-2 device capable of translating between different ethernet technologies.

#### c) (1.) Explain how the switch table of n is built. ~~(2.) Write down the table assuming recent communication between all other nodes.~~
- The table is initially empty
- When a frame arrives on one of the interfaces and its destination isn't in the table, the switch forwards copies of the frame on all its interfaces except the one it arrived on.
- for each frame received, the switch stores in its table the source LAN address, the interface on which the frame arrived and the current time.

### Problem 2
#### a) What are the main functions of (1.) the data plane and (2.) the control plane?
1. The control plane defines how packets are forwarded; Routing table creation is part of the control plane.
1. The data plane is the processes that actually forward the packets in accordacne with the control plane.

#### b) What is the difference between switching and routing?
Switching connects multiple devices on the same network, while routing connects multiple networks together.
Switches just connect devices together, but routers work at the network layer to find the shortest path for a packet across the networks.

#### c) What are the characteristics of the network service model?
It defines the properties of the channel connecting the transport layers of two communicating hosts, in terms of:
   - Service reliability
   - Received packets ordering compared to transmitted
   - Time between two consecutive sent or received packets
   - Network congestion feedback

### Problem 3
#### a) Draw a block diagram showing the router's architecture.
![](README.d/ass4-prob3-route-arch.png)

#### b) What are the advantages and disadvantages of different types of switching fabrics?
| fabric type     | advantages | disadvantages |
|-----------------|------------|---------------|
| bus             | No processor intervention | - forwards only one packet at a time </br> - all packets are queued when the bus is busy |
| interconnection | - minimal processor intervention</br> - less idle time than a single bus | - more busses are used (2N busses to connect N ports)</br> - non-zero processing and idle time |
| memory          | The most reliable method with flexible scheduling modes | - control happens fully in CPU</br> - packets are copied instead of forwarded which is slower and less efficient |

#### c) Describe how the routing table entries are stored, and explain its effect on the processing time.
The are stored as entries pointing the next hop required to reach a destination IP, as well as the No. of hops till this IP is reached. This allows them to be stored as binary tress where closer together routers (with similar IP addresses or in subnetworks of the same WAN) are grouped together in a subtree and are searchable in O(n) time.

#### d) Explain how a queue could build up at both the input ports and the output ports of a router.
- Input queueing can occur when:
   - the switching fabric is slower than the rate at which input packets are received.
   - multiple packets at the input ports are destined to the same output poty
   - a packet at an input id destined to an empty output port, but is preceded by another packet destined to a busy one, which is known as Head-of-Line blocking.
- Output queueing can occur when:
   - multiple input packets are destined to a single output port
   - the switching fabric is slower than the incoming traffic.

#### e) What is Head-of-Line blocking? What scenario will lead to it?
It's when a packet is queued at an input port despite being destined to a an empty output port. It happens only in the case of input buffering when a packet is preceded by a another on the same input port that is waiting on a busy output port.

### Problem 4
#### a) What is the maximum numbers that can be used with each class of IPv4?
Class A: 2<sup>7</sup>,
Class B: 2<sup>14</sup>,
Class C: 2<sup>21</sup>,
Class D: 2<sup>28</sup>
#### b) What are the address types of IPv6?
Unicast, anycast and multicast.

#### c) What is the advantage of the tunneling approach over the dual stack approach when transistioning from IPv4 to IPv6? Give an example to explain your answer.
Tunneling maintains all the information in an IPv6 packet headerm such as the flow label, which is a new header field that dual stack transmission would strip away.

#### ~~d)~~
### ~~Problem 5~~