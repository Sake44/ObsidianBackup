The figure below shows the physical path that data takes down a sending end system’s protocol stack, up and down the protocol stacks of an intervening link-layer switch and router, and then up the protocol stack at the receiving end system.
Similar to end systems, routers and link-layer switches organize their networking hardware and software into layers. But routers and link-layer switches do not implement all of the layers in the protocol stack; they typically implement only the bottom layers. As shown in the figure below, link-layer switches implement layers 1 and 2; routers implement layers 1 through 3.

![[Pasted image 20250530114312.png]]
To figure out what is happening through all the layer, follow this:
1. At the sending host, an application-layer message is passed to the transport layer. In the simplest case, the transport layer takes the message and appends additional information (so-called transport-layer header information) that will be used by the receiver-side transport layer.
2. The transport layer then passes the segment to the network layer, which adds network-layer header information such as source and destination end system addresses, creating a network-layer datagram. 
3. The datagram is then passed to the link layer, which (of course!) will add its own link-layer header information and create a link-layer frame. 
Thus, we see that at each layer, a packet has two types of fields: **header fields and a payload field**. The payload is typically a packet from the layer above.
