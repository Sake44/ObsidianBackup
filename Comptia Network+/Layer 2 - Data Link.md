The data link layer (layer 2) is responsible for transferring data between nodes on the same logical segment. At the Data Link layer, a segment is one where all nodes can send traffic to one another using hardware addresses.
Relatively few networks are based on directly connecting hosts together. Rather than making hosts establish direct links with one another, each host is connected to a central node, such as a switch or a wireless access point.
The data link layer organizes the stream of bits arriving from the physical layer into structured units called frames. Each frame contains a network layer packet as its payload. The data link layer adds control information to the payload in the form of header fields. These fields include source and destination hardware addresses, plus a basic error check to test if the frame was received intact.

Devices that operate at the data link layer include: 
- Network Adapter or NIC: An NIC joins an end system host to network media (cabling or wireless) and enables it to communicate over the network by assembling and disassembling frames.
- Bridge: A bridge is a type of intermediate system that joins physical network segments while minimizing the performance reduction of having more nodes on the same network. A bridge has multiple ports, each of which functions as a network interface.
- Switch: An advanced type of bridge with many ports. A switch creates links between large numbers of nodes more efficiently.
- An AP allows nodes with wireless network cards to communicate and creates a bridge between wireless networks and wired ones.

Let's see next layer: [[Layer 3 - Network]].