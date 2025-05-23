End systems connect into the Internet via an access ISP.

>Note that the access ISP does not have to be a telco or a cable company; instead it can be, for example, a university (providing Internet access to students, staff, and faculty), or a company (providing access for its employees).

In order to understand today’s Internet network structure, let’s incrementally build a series of network structures, with each new structure being a better approximation of the complex Internet that we have today. Recall that the overarching goal is to **interconnect the access ISPs so that all end systems can send packets to each other.**
Our first network structure, *Network Structure 1*, interconnects all of the access ISPs with a *single global transit ISP*. Our (imaginary) global transit ISP is a network of routers and communication links that not only spans the globe, but also has at least one router near each of the hundreds of thousands of access ISPs.
Since the access ISP pays the global transit ISP, the access ISP is said to be a **customer** and the global transit ISP is said to be a **provider**.
Now if some company builds and operates a global transit ISP that is profitable, then it is natural for other companies to build their own global transit ISPs and compete with the original global transit ISP.
This leads to Network Structure 2, which **consists of the hundreds of thousands of access ISPs and multiple global transit ISPs.** The access ISPs certainly prefer Network Structure 2 over Network Structure 1 since they can now **choose among the competing global transit providers as a function of their pricing and services.** Note, however, that the global transit ISPs themselves must interconnect: Otherwise access ISPs connected to one of the global
transit providers would not be able to communicate with access ISPs connected to the other global transit providers.
**Network Structure 2, just described, is a two-tier hierarchy with global transit providers residing at the top tier and access ISPs at the bottom tier.**

> For example, in China, there are access ISPs in each city, which connect to provincial ISPs, which in turn connect to national ISPs, which finally connect to tier-1 ISPs.

To build a network that more closely resembles today’s Internet, we must add **points of presence** (PoPs), **multi-homing**, **peering**, and **Internet exchange points** (IXPs) to the hierarchical *Network Structure 3*.
PoPs exist in all level of the hierarchy, except for the bottom (access ISP) level. 

- A **PoP** is simply a group of one or more routers (at the same location) in the provider's network where customer ISPs can connect into the provider ISP.
- **Multi-home** is about to connect to two or more provider ISPs. So, for example, an access ISP may multi-home with two regional ISPs, or it may multi-home with two regional ISPs and also with a tier-1 ISP.
- As we just learned, customer ISPs pay their provider ISPs to obtain global Internet interconnectivity. To reduce these costs, a pair of nearby ISPs at the same level of the hierarchy can **peer**, that is, they can directly connect their networks together so that all the traffic between them passes over the direct connection rather than through upstream intermediaries.
- Along these same lines, a third-party company can create an **Internet Exchange Point** (IXP), which is a meeting point where multiple ISPs can peer together. An IXP is typically in a stand-alone building with its own switches.
We refer to this ecosystem—consisting of access ISPs, regional ISPs, tier-1 ISPs, PoPs, multi-homing, peering, and IXPs—as Network Structure 4.

We now finally arrive at Network Structure 5, which describes today’s Internet. Network Structure 5, builds on top of Network Structure 4 by adding **content-provider networks**. Google is currently one of the leading examples of such a content-provider network.
Google has a great variety of major data center distributed across almost each continent. 
Additionally, Google has smaller data centers, each with a few hundred servers; these smaller data centers are often located within IXPs. The Google data centers are all interconnected via Google’s **private TCP/IP network**, which spans the entire globe but is nevertheless separate from the public Internet. Importantly, the Google private network only
carries traffic to/from Google servers.
![[Screenshot from 2025-05-23 09-29-26.png]]


