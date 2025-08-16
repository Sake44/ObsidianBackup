At the transport layer—also known as the end-to-end or host-to-host layer—the content of the packets becomes significant. Any given host on a network will be communicating with many other
hosts using many different types of networking data. One of the functions of the transport layer is to identify each type of network application by assigning it a port number.
At the network and data link layers, the port number is ignored—it becomes part of the
data payload and is invisible to the routers and switches that implement the addressing
and forwarding functions of these layers. At the receiving host, each segment is
decapsulated, identified by its port number, and passed to the relevant handler at the
application layer.
The transport layer can also implement reliable data delivery mechanism, so every data lost or damaged packets are resent.
