The upper layers of the OSI model are less clearly associated with distinct realworld protocols. These layers collect various functions that provide useful interfaces between software applications and the transport layer.

## Layer 5 - Session

Most application protocols require the exchange of multiple messages between the client and server. This exchange of such a sequence of messages is called a session or dialog. The session layer (layer 5) represents functions that administer the process of establishing a dialog, managing data transfer, and then ending (or tearing down) the session.

### Layer 6 - Presentation

The presentation layer (layer 6) transforms data between the format required for the network and the format required for the application. **For example, the presentation layer is used for character set conversion, such as between American Standard Code for Information Interchange (ASCII) and Unicode.**

### Layer 7 - Application

The application layer (layer 7) is at the top of the OSI stack. An applicationlayer protocol doesn’t encapsulate any other protocols or provide services to any protocol. Application-layer protocols provide an interface for software programs on network hosts that have established a communications channel through the lower-level protocols to exchange data.

#### OSI Model summary
![[Pasted image 20250816193121.png]]