# Introduction
The OSI model breaks the data communication process into discrete layers.

## Open System Interconnection Model
A network is **two or more computer** systems that are linked by a transmission medium and share one or more protocols that enable them to exchange data. You can think of any network in terms of nodes and links. The nodes are devices that send, receive, and forward data and the links are the communications pathways between them.

The International Organization for Standardization (ISO) developed the Open Systems Interconnection (OSI) reference model to promote understanding of how components in a network system works. It does this by separating the function of hardware and software components to seven discrete layers.
![[Pasted image 20250523171114.png]]
The OSI model is not a standard or a specification; it serves as a functional guideline for designing network protocols, software, and appliances and for troubleshooting networks.

## Data Encapsulation and Decapsulation

A network protocol is a set of rules for exchanging data in a structured format.
A network protocol has two principal functions:

- Addressing: Describing where data messages should go.
- Encapsulation: Describing how data messages should be packaged for transmission. Encapsulation is like an envelope for a letter, with the distinction that each layer requires its own envelope. At each layer, the protocol adds fields in a header to whatever data (payload) it receives from an application or other protocol.
A network will involve the use of many dif ferent protocols operating at differentlayers of the OSI model. At each layer, for two nodes to communicate they must be running the same protocol. The protocol running at each layer communicates with its equivalent (or peer) layer on the other node. This communication between nodes at the same layer is described as a same layer interaction.

![[Pasted image 20250702094415.png]]

At each level (except the physical layer), the sending node adds a header to the data payload, forming a “chunk” of data called a protocol data unit (PDU). This is the process of encapsulation.

