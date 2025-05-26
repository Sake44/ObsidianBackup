Ideally, we would like Internet services to be able to move as much data as we want between any two end systems, instantaneously, without any loss of data. Alas, this is a lofty goal, one that is unachievable in reality. Instead, computer networks necessarily constrain
throughput (**the amount of data per second that can be transferred**) between end systems, introduce delays between end systems, and can actually lose packets.

## Overview of Delay in Packet-Switched Networks
Recall that a packet starts in a host (the source), passes through a series of routers, and ends its journey in another host (the destination). As a packet travels from one node (host or router) to the subsequent node (host or router) along this path, the packet suffers from several types of delays at each node along the path. The most important of these delays are:
- Nodal processing delay
- Queuing delay
- Transmission delay
- Propagation delay

### Types of Delay
Let's characterize the nodal delay at router A.
Note that router A has an outbound link leading to router B. This link is preceded by a queue (also known as a buffer). When the packet arrives at router A from the upstream node, router A examines the packet’s header to determine the appropriate outbound link for the packet and then directs the packet to this link.

>A packet can be transmitted on a link only if there is no other packet currently being transmitted on the link and if there are no other packets preceding it in the queue; if the link is c­ urrently busy or if there are other packets already queued for the link, the newly arriving packet will then join the queue.

![[Screenshot from 2025-05-23 10-01-32.png]]

#### Processing Delay
The time required to examine the packet’s header and determine where to direct the packet is part of the processing delay.
Processing delays in high-speed routers are typically on the **order of microseconds or less**. After this nodal processing, the router directs the packet to the queue that precedes the link to router B.
#### Queuing Delay
At the queue, the packet experiences a queuing delay as it **waits to be transmitted onto the link**. The length of the queuing delay of a specific packet will depend on the number of earlier-arriving packets that are queued and waiting for transmission onto the link.

#### Trasmission Delay
Assuming that packets are transmitted in a first-come-first-served manner, as is common in packet-switched networks, our packet can be transmitted only after all the packets that have arrived before it have been transmitted.

The transmission delay is L/R. This is the amount of time required to push (that is, transmit) all of the packet’s bits into the link.

#### Propagation Delay
Once a bit is pushed into the link, it needs to propagate to router B. The time required to propagate from the beginning of the link to router B is the propagation delay.
**The propagation delay is the distance between two routers divided by the propagation speed.** That is, the propaga tion delay is d/s, where d is the distance between router A and router B and s is the propagation speed of the link.

### Comparing Transmission and Propagation Delay
The transmission delay is the amount of time required for the router to push out the packet; it is a function of the packet’s length and the transmission rate of the link, but has nothing to do with the distance between the two routers. The propagation delay, on the other hand, is the time it takes a bit to propagate from one router to the next; it is a function of the distance between the two routers, but has nothing to do with the packet’s length or the transmission rate of the link.

If we let dproc, dqueue, dtrans, and dprop denote the processing, queuing, transmission,
and propagation delays, then the total nodal delay is given by:

```
dnodal = dproc + dqueue + dtrans + dprop
```

### Queuing Delay and Packet Loss
