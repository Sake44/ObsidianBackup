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
Unlike the other three delays (namely, dproc, dtrans, and dprop), the queuing delay can vary from
packet to packet. For example, if 10 packets arrive at an empty queue at the same time, the first packet transmitted will suffer no queuing delay, while the last packet transmitted will suffer a relatively large queuing delay.
Let **a** denote the average rate at which packets arrive at the queue (a is in units of packets/sec). Recall that **R** is the **transmission rate**; that is, it is the rate (in bits/sec) at which bits are pushed out
of the queue. Also suppose, for simplicity, that all packets consist of **L** bits. Then the average rate at which bits arrive at the queue is **La bits/sec**. Finally, assume that the queue is very big, so that it can hold essentially an infinite number of bits. The ratio **La/R**, called the **traffic intensity**, often plays an important role in estimating the extent of the queuing delay. If **La/R > 1**, then the average rate at which bits arrive at the queue exceeds the rate at which the bits can be transmitted from the queue. In this unfortunate situation, the queue will tend to increase without bound and the queuing delay will approach infinity! Therefore, one of the golden rules in traffic engineering
is: *Design your system so that the traffic intensity is no greater than 1.*

#### Packet Loss
A queue preceding a link has finite capacity, although the queuing capacity greatly depends on the router design and cost. Because the queue capacity is finite, packet delays do not really approach infinity as the traffic intensity approaches 1. Instead, a packet can arrive to find a full queue. With no place to store such a packet, a router will drop that packet; that is, the packet will be lost.
From an end-system viewpoint, a packet loss will look like a packet having been transmitted into the network core but never emerging from the network at the destination. The fraction of lost packets increases as the traffic intensity increases.

### End-to-End Delay
The end to end delay is calculated as 
```
dend-end = N(dproc + dtrans + d)
```

#### Traceroute
Traceroute is a simple program that can run in any Internet host. When the user specifies a destination hostname, the program in the source host sends multiple, special packets toward that destination. As these packets work their way toward the destination, they pass through a series of routers. When a router receives one of these special packets, it sends back to the source a short message that contains the name and address of the router.

### Throughput in Computer Networks
In addition to delay and packet loss, another critical performance measure in computer networks is end-to-end throughput. To define throughput, consider transferring a large file from Host A to Host B across a computer network.
The instantaneous throughput at any instant of time is the rate (in bits/sec) at which Host B is receiving the file.

More generally the throughput depends not only on the transmission rates of the links along the path, but also on the intervening traffic. In particular, a link with a high transmission rate may nonetheless be the bottleneck link for a file transfer if many other data flows are also passing through that link.
