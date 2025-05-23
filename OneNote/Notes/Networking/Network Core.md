We can define **Network Core** as the mesh of packet switches and links that interconnect the Internet's end system.
![[Screenshot from 2025-05-21 18-55-02.png]]

## Packet Switching

In a network application, end systems exchange messages with each other. Messages can contain anything the application designer wants.
To send a message from a source end system to a destination end system, the source breaks long messages into smaller chunks of data known as **packets**. Between source and destination, each packet travels through communication links and packet switches (for which there are two predominant types, routers and link-layer switches).


### Store-and-Forward Transmission

Most packet switches use **store-and-forward** transmission at the inputs to the links. Store-and-forward transmission means that the packet switch must receive the entire packet before it can begin to transmit the first bit of the packet onto the outbound link.

![[Screenshot from 2025-05-22 09-19-53.png]]
A router will typically have many incident links, since its job is to switch an incoming packet onto an outgoing link; in this simple example, the router has the rather simple task of transferring a packet from one (input) link to the only other attached link. In this example, the source has three packets, each consisting of L bits, to send to the destination. At the snapshot of time shown in Figure 1.11, the source has transmitted some of packet 1, and the front of packet 1 has already arrived at the router. Because the router employs store-and-forwarding, at this instant of time, the router cannot transmit the bits it has received; instead it must first **buffer** (i.e., “store”) the packet’s bits. Only after the router has received
all of the packet’s bits can it begin to transmit (i.e., “forward”) the packet onto the outbound link.

The source begins to transmit at time 0; **at time L/R seconds, the source has transmitted the entire packet, and the entire packet has been received and stored at the router** (since there is nopropagation delay). At time L/R seconds, since the router has just received the entire packet, it can begin to transmit the packet onto the outbound link towards the destination; at time 2L/R, the router has transmitted the entire packet, and the entire packet has been received by the destination. Thus, the total delay is 2L/R.

### Queuing Delays and Packet Loss
Each packet switch has multiple links attached to it. For each attached link, the packet switch has an **output buffer** (also called an output queue), which stores packets that the router is about to send into that link. **The output buffers play a key role in packet switching. If an arriving packet needs to be transmitted onto a link but finds the link busy with the transmission of another packet, the arriving packet must wait in the output buffer.** Thus, in addition to the store-and-forward delays, packets suffer output buffer queuing delays.

![[Screenshot from 2025-05-22 09-54-19.png]]

Since the amount of buffer space is finite, an arriving packet may find that the buffer is completely full with other packets waiting for transmission. In this case, **packet loss** will occur.

### Forwarding Tables and Routing Protocols
How does the router determine which link it should forward the packet onto?
In the Internet, every end system has an address called an IP address. When a source end system wants to send a packet to a destination end system, **the source includes the destination’s IP address in the packet’s header.**
More specifically, **each router has a forwarding table that maps destination addresses (or portions of the destination addresses) to that router’s outbound links.** When a packet arrives at a router, the router examines the address and searches its forwarding table, using this destination address, to find the appropriate outbound link. The router then directs the packet to this outbound link.

How do forwarding tables get set? Are they configured by hand in each and every router, or does the Internet use a more automated procedure?
**The Internet has a number of special routing protocols that are used to automatically set the forwarding tables.** A routing protocol may, for example, determine the shortest path from each router to each destination and use the shortest path results to configure the forwarding tables in the routers.

## Circuit Switching
In **circuit-switched** networks, the resources needed along a path (buffers, link transmission rate) to provide for communication between the end systems are reserved for the duration of the communication session between the end systems. In packet-switched networks, theser resources are *not reserved*. a **session’s messages** use the resources on demand and, as a consequence, may have to wait (that is, queue) for access to a communication link. **Traditional telephone networks are examples of circuit-switched networks. 
Before the sender can send the information, the network must establish a connection between the sender and the receiver.** This is a bona fide connection for which the switches on the path between the sender and receiver maintain connection state for that connection. In the jargon of telephony, this connection is called a circuit.
![[Screenshot from 2025-05-22 11-33-34.png]]

### Multiplexing in Circuit-Switched Networks
A circuit in a link is implemented with either **frequency-division multiplexing** (FDM) or **time-division multiplexing** (TDM). With FDM, the frequency spectrum of a link is divided up among the connections established across the link. Specifically, the link dedicates a frequency band to each connection for the d­ uration of the connection.
For a **TDM** link, time is divided into frames of fixed duration, and each frame is divided into a fixed number of time slots. **When the network establishes a connection across a link, the network dedicates one time slot in every frame to this connection.** These slots are dedicated for the sole use of that connection, with one time slot available for use (in every frame) to transmit the connection’s data.

### Packet Switching Versus Circuit Switching
Critics of packet switching have often argued that **packet switching is not suitable for realtime services** (for example, telephone calls and video conference calls) because of its variable and unpredictable end-to-end delays.
Proponents of packet switching argue that it **offers better sharing of transmission capacity than circuit switching and it is simpler, more efficient, and less costly to implement than circuit switching.**

