## Protocol
A network protocol is similar to a human protocol, except that the entities exchanging messages and taking actions are hardware or software components of some device.
All activity in the Internet that involves two or more communicating remote entities is governed by a protocol.

> A protocol defines the format and the order of messages exchanged between two
   or more communicating entities, as well as the actions taken on the transmission
   and/or receipt of a message or other event.

## The network edge
Recall from the previous section that in computer networking jargon, the computers and other devices connected to the Internet are often referred to as **end system**. Below an image of end system interaction:
![[Screenshot from 2025-05-21 07-26-04 1.png]]

End systems are also referred to as **hosts** because they host (that is, run) application programs such as a Web browser program, a Web server program, an e-mail client program.
Hosts are sometimes further divided into two categories: clients and servers. 
Informally, clients tend to be desktops, laptops, smartphones, and so on, whereas
servers tend to be more powerful machines that store and distribute Web pages,
stream video, relay e-mail, and so on.

### Access Network
Having considered the applications and end systems at the “edge of the network,” let’s next consider the access network—the network that physically connects an end system to the first router (also known as the “edge router”) on a path from the end system to any other distant end system.

#### Home access: DSL, Cable, FTTH, and 5G Fixed Wireless
The two most prevalent types of broadband residential access are digital subscriber line (DSL) and cable. A residence typically obtains #DSL Internet access from the same local telephone company (telco) that provides its wired local phone access.

As shown in the image below each customer’s DSL modem uses the existing telephone line exchange data with a digital subscriber line access multiplexer (DSLAM) located in the telco’s local central office (CO).

![[Screenshot from 2025-05-21 10-16-52.png]]

The residential telephone line carries both data and traditional telephone signals simultaneously, which are encoded at different frequencies:

• A high-speed downstream channel, in the 50 kHz to 1 MHz band
• A medium-speed upstream channel, in the 4 kHz to 50 kHz band
• An ordinary two-way telephone channel, in the 0 to 4 kHz band

This approach makes the single DSL link appear as if there were three separate links, so that a telephone call and an Internet connection can share the DSL link at the same time.

Although DSL cable networks currently represent the majority of residential broadband access, an up-and-coming technology that provides even higher speeds is **fiber to the home** (FTTH).



