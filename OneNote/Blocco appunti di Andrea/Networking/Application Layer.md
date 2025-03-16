**ACK flag:** ==One of the TCP control flags. ACK is short for acknowledge. A value of one in this field means that the acknowledgment number field should be examined==  
**Acknowledgement number:** ==The number of the next expected segment in a TCP sequence==  
**Application layer:** ==The layer that allows network applications to communicate in a way they understand==  
**Application layer payload:** ==The entire contents of whatever data applications want to send to each other==  
**CLOSE:** ==A connection state that indicates that the connection has been fully terminated, and that no further communication is possible==  
**CLOSE_WAIT:** ==A connection state that indicates that the connection has been closed at the TCP layer, but that the application that opened the socket hasn't released its hold on the socket yet==  
**Connection-oriented protocol:** ==A data-transmission protocol that establishes a connection at the transport layer, and uses this to ensure that all data has been properly transmitted==  
**Connectionless protocol:** ==A data-transmission protocol that allows data to be exchanged without an established connection at the transport layer. The most common of these is known as UDP, or User Datagram Protocol==  
**Data offset field:** ==The number of the next expected segment in a TCP packet/datagram==  
**Demultiplexing:** ==Taking traffic that's all aimed at the same node and delivering it to the proper receiving service==  
**Destination port:** ==The port of the service the TCP packet is intended for==  
**ESTABLISHED:** ==Status indicating that the TCP connection is in working order, and both sides are free to send each other data==  
**FIN:** ==One of the TCP control flags. FIN is short for finish. When this flag is set to one, it means the transmitting computer doesn't have any more data to send and the connection can be closed==    
**FIN_WAIT:** ==A TCP socket state indicating that a FIN has been sent, but the corresponding ACK from the other end hasn't been received yet==  
**Firewall:** ==It is a device that blocks or allows traffic based on established rules==   
**FTP:** ==An older method used for transferring files from one computer to another, but you still see it in use today==  
**Handshake:** ==A way for two devices to ensure that they're speaking the same protocol and will be able to understand each other==  
**Instantiation:** ==The actual implementation of something defined elsewhere==  
**Listen:** ==It means that a TCP socket is ready and listening for incoming connections==  
**Multiplexing:** ==It means that nodes on the network have the ability to direct traffic toward many different receiving services==  
**Options field:** ==It is sometimes used for more complicated flow control protocols==  
**Port:** ==It is a 16-bit number that's used to direct traffic to specific services running on a networked computer==  
**Presentation layer:** ==It is responsible for making sure that the unencapsulated application layer data is actually able to be understood by the application in question==  
**PSH flag:** ==One of the TCP control flags. PSH is short for push. This flag means that the transmitting device wants the receiving device to push currently- buffered data to the application on the receiving end as soon as possible==  
**RST flag:** ==One of the TCP control flags. RST is short for reset. This flag means that one of the sides in a TCP connection hasn't been able to properly recover from a series of missing or malformed segments==  
**Sequence number:** ==A 32-bit number that's used to keep track of where in a sequence of TCP segments this one is expected to be==  
**Server or Service:** ==A program running on a computer waiting to be asked for data==  
**Session layer:** ==The network layer responsible for facilitating the communication between actual applications and the transport layer==  
**Socket:** ==The instantiation of an endpoint in a potential TCP connection==  
**Source port:** ==A high numbered port chosen from a special section of ports known as ephemeral ports==  
**SYN flag:** ==One of the TCP flags. SYN stands for synchronize. This flag is used when first establishing a TCP connection and make sure the receiving end knows to examine the sequence number field==  
**SYN_RECEIVED:** ==A TCP socket state that means that a socket previously in a listener state, has received a synchronization request and sent a SYN_ACK back==  
**SYN_SENT:** ==A TCP socket state that means that a synchronization request has been sent, but the connection hasn't been established yet==  
**TCP checksum:** ==A mechanism that makes sure that no data is lost or corrupted during a transfer==   
**TCP segment:** ==A payload section of an IP datagram made up of a TCP header and a data section==  
**TCP window:** ==The range of sequence numbers that might be sent before an acknowledgement is required==  
**URG flag:** ==One of the TCP control flags. URG is short for urgent. A value of one here indicates that the segment is considered urgent and that the urgent pointer field has more data about this==  
**Urgent pointer field:** ==A field used in conjunction with one of the TCP control flags to point out particular segments that might be more important than others==