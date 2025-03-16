**One-Way Trust**  
==A one-way trust is a unidirectional authentication path created between two domains. This one-way trust path between Domain A and Domain B enables users in Domain A to access resources in Domain B. However, users in Domain B cannot access resources in Domain A. Some one-way trusts can be either a nontransitive trust or a transitive trust, depending on the type of trust that is created.==  
**Two-Way Trust**  
==In a two-way trust, Domain A trusts Domain B, and Domain B trusts Domain A. This means that authentication requests can be passed between the two domains in both directions. Some two-way relationships can be either nontransitive or transitive depending on the type of trust that is created.==  
**Transitive Trust**  
==Transitive trust is the extension of trust between two parties to areas outside or beyond the original trust relationship. It can be defined in two ways:==

- ==If Domain A trusts Domain B, and Domain B trusts Domain C, then Domain A could have transitive trust with Domain C.==
- ==The other approach is used in some directory-based products where a subdirectory inherits trust from the parent directory.==

**Zero Trust**  
==The idea of “zero trust” comes from the world of network security. In a zero-trust environment, no entity, whether inside or outside the network perimeter, is considered trusted by default.==
 
==Key principles of the zero-trust model in network security include:==

- _Verifying every access request._ ==All users, devices, and applications attempting to access resources must be authenticated and authorized before access is granted. This authentication and authorization process is continuous and granular, occurring at every access attempt and location.== 
- _Least privilege access._ ==Access rights are assigned based on the principle of least privilege, meaning users and devices are granted only the minimum level of access necessary to perform their tasks. This reduces the potential impact of a security breach or insider threat.==
- _Microsegmentation._ ==Network segmentation is implemented at a granular level to create smaller security perimeters around individual resources or data sets. This helps contain security breaches and prevents lateral movement by attackers within the network.==
- _Continuous monitoring and inspection._ ==Zero trust networks employ continuous monitoring and inspection of network traffic, user behavior, and security controls to detect and respond to threats in real-time. This proactive approach helps identify anomalies and potential security breaches early.==
- _Encryption and data protection._ ==Data is encrypted both in transit and at rest to protect it from unauthorized access. Strong encryption algorithms and protocols are used to ensure the confidentiality and integrity of data.==