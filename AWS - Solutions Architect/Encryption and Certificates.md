Encryption refers to the process of using cryptographic math procedures, called algorithms, with keys to transform data into messages that can only be read using the key.

### Asymmetric Encryption
**Asymmetric, or public key,** **encryption** uses algorithms based on mathematical problems that are relatively straightforward to perform in one direction, but cannot be conveniently reversed. An encryption scheme is called asymmetric if it uses one key to encrypt data, and a different but mathematically related key to decrypt data.
![[Pasted image 20251028104224.png]]
### Symmetric encryption
**Symmetric** encryption refers to encryption using algorithms, in which the same key is used to both encrypt and decrypt data. Symmetric encryption requires that all intended message recipients have access to a shared key.
### Envelope Encryption
As mentioned previously, data is encrypted by applying a cryptographic algorithm with a key to plaintext data. A key that is used to encrypt data is called a **data key**. This process protects the underlying data, but it produces another question. **H****ow do you protect the data key?** 

One answer is to encrypt the data key with a separate key, called a **wrapping key,** or **key encryption key.** The process of encrypting the data key with another key is called **envelope encryption.**
![[Pasted image 20251028104432.png]]

## AWS KMS (Key Management System)
AWS KMS can help streamline challenges normally associated with managing encryption keys and encrypting **data at rest** in AWS. AWS KMS is primarily designed as a sort of vending machine for keys. It offers a variety of cryptographic operations for the keys it creates, such as using them to decrypt and encrypt data.
There is no mechanism for anyone, including AWS service operators, to view, access, or export plaintext key material from AWS KMS keys. Plaintext customer key material is only used for cryptographic operations requested by customers, within hardware security modules (HSMs) controlled by AWS KMS.

The data generated and transferred within modern applications is generally encrypted in three phases. Often, your goal will be to achieve **end-to-end** encryption, or encryption of data throughout its lifecycle, until it is ultimately stored.   
To achieve this goal, you can encrypt data at the **application level** before it's transferred, or encrypt the data **in transit** and **at rest.**  
In the context of a typical modern web application, data can be encrypted at the following points:
 
- **Application level:** Consider a transaction generated in a user's browser while using a web application. The app owner can use AWS encryption libraries in their application to encrypt the transaction record before it is sent over the public internet.

**In transit:** The app owner could also choose to encrypt the transaction as it is transferred from the client application to their application servers.

- **At rest**: The application servers process the transaction and update a database accordingly. The app owner can encrypt the underlying storage supporting the database to mitigate damage in case of a compromise.
 ![Infographic categorizing AWS offerings by the encryption phase they are designed to support. Details in following paragraph.](Exported%20image%2020250315115753-0.png)

The AWS Encryption SDK, AWS Database Encryption SDK, and Amazon S3 Encryption Client are used to encrypt data at the **application level** before it is sent across networks. AWS Certificate Manager (ACM) and AWS Private Certificate Authority are used to encrypt **data in transit** across networks. AWS Key Management Service (AWS KMS) and AWS CloudHSM are used to encrypt **data at rest** or data stored in persistent locations.

AWS KMS can help streamline challenges normally associated with managing encryption keys and encrypting **data at rest** in AWS. AWS KMS is primarily designed as a sort of vending machine for keys. It offers a variety of cryptographic operations for the keys it creates, such as using them to decrypt and encrypt data. You can create customer managed keys or use AWS managed keys to encrypt sensitive data stored on AWS without concern for redundancy, availability, or managing hardware.
 
AWS KMS can add value to your operations if you have any of the following use cases:
 
- To encrypt data at rest stored in the AWS Cloud with over 100 AWS services, such as Amazon EBS or Amazon S3 - To perform as a key encryption key, or **wrapping key,** provider for the AWS Encryption SDK when performing client-side encryption
- To digitally sign and verify data using asymmetric key pairs
- To generate and verify message authentication codes (MACs) - To generate random numbers for cryptographic applications
   

### Key policies
A key policy is a resource policy for an AWS KMS key. Key policies are the primary way to control access to AWS KMS keys. Every AWS KMS key must have exactly one key policy. The statements in the key policy determine who has permission to use the AWS KMS key and how they can use it.  
You can use AWS Identity and Access Management (IAM) policies in combination with key policies to administer permissions for using keys. To complete an operation on a key, the key policy must permit the principal to do so without denial from the IAM policies attached to the principal.
 
### Grants
A grant is a policy instrument that provisions permissions for AWS principals to use AWS KMS keys for a variety of actions, ranging from cryptographic operations to viewing the key. Grants are often used for temporary, just-in-time permissions because you can create one, use its permissions, and delete it without changing your key policies or IAM policies.

|Key consideration|Customer managed keys|AWS managed keys|
|---|---|---|
|Key policy|Managed by customer|Managed by AWS|
|Key rotation|Optional, managed by the customer|Mandatory, every year|
|Import custom key material|Optional, managed by the customer|N/A|
|Cost|$1 per month, plus charges on API calls|Charges on API calls|
|Usage auditing|Customer AWS CloudTrail logging|Customer AWS CloudTrail logging|

**Rotating your keys**
 
Cryptographic best practices discourage extensive reuse of keys that encrypt data directly, such as the data keys that other services request from AWS KMS. When 256-bit data keys encrypt massive amounts of data, they can become **exhausted**. The ciphertext produced by an exhausted key will show subtle patterns that clever, malicious actors can exploit to discover the bits in the key.

## AWS CloudHSM
 
HSMs, or hardware security modules, are computing devices that perform cryptographic operations and provide secure storage for cryptographic keys. Customers might have strict security requirements to maintain control over the HSMs that generate and store their encryption keys.
### When should you consider using CloudHSM?
CloudHSM can add value to your operations if you have any of the following use cases:
 
- To provision and manage the HSMs that generate and store your encryption keys
- To implement encryption instead of AWS KMS, if your applications don't support API calls
- To configure SSL offloading by reducing the cryptographic workload on your web servers
- To store the Transparent Data Encryption (TDE) key for your Oracle databases

![File is sent with a signature to help ensure data integrity. Details in text.](Exported%20image%2020250315115754-1.png)
## Hashing and Signing
Hashes and digital signatures are used to augment the encryption of **data in transit**.
These applications of cryptography provide a means for web entities to confirm the **integrity** of data and authenticate it across networks through the use of **digital certificates**.

### Hashing
**Hashing** is another application of cryptography in which an algorithm is applied to a message to generate a randomized string of bits. However, unlike encryption, hashing is a one-way operation. The hash material cannot be converted back to **plaintext**.

Because hash algorithms will always return one output if given the same input, hashing is often used to verify that two values match.
### Signing
A **digital signature** is a cryptographic technique that uses **public key**, or **asymmetric** cryptography to validate the **authenticity** and **integrity** of a digital object. A digital signature is effectively a **hash** value of a digital object, such as a file or message, which is encrypted by a **private key**.
#### How Digital Signature work? 
The nature of **public key** **cryptography** makes it possible to trust digitally signed objects while interacting with the internet. If the recipient has access to the public key corresponding to the private key that created the signature, the recipient can decrypt the signature.
![[Pasted image 20251028105556.png]]
## Public Key Infrastructure (PKI)
A digital certificate is an electronic credential that proves the authenticity of a user, device, server, or website. This form of **authentication** uses **public key encryption** to validate identities communicating over networks. These certificates contain an expiration date and information about the holder or **subject**, including the domain name and organization. They also contain the issuing **certificate authority** and their **digital signature**.
Modern digital certificates most commonly follow the x.509 standard, which binds the identifying information to a **public-private key pair**.
### What are Certificate Authorities? (CA)
A **certificate authority** **(CA)** is an entity that issues and, if necessary, revokes digital certificates to parties communicating across networks.
### Publicly trusted CA
A **publicly trusted CA, or public CA,** earns public trust by working with major browsers, operating systems, and device manufacturers to satisfy rigorous security requirements.
### Privately trusted CA
A **privately trusted CA, or private CA,** secures communication among internal devices and web systems from within an organization or group. These CAs do not build public trust by meeting requirements from external stakeholders; therefore, do not issue **public certificates**.
You might use a **private CA** to create **private certificates** for internal resources to authenticate and communicate with each other.
### How do Certificates help encrypt data in transit? 
SSL/TLS encryption works because of the **authentication** offered by digital certificates. If a client trusts the CA who issued the certificate for a web server, and the certificate is legitimate, then the client can trust that server.
![[Pasted image 20251028111011.png]]
### What are certificate hierarchies? 
Most certificate authorities operate within a hierarchy, in which a **root CA** exists as an ultimate source of truth for an organization. A root CA holds a public-private key pair for signing certificates and a **root certificate**. The root certificate identifies the server as the **root CA** and binds it to its private key.
The root might have **subordinate,** or **intermediate CAs** existing as separate servers to create a logical separation of duties. The root CA can sign **CA certificates** for subordinate CAs, which authorizes them as CAs to perform further signing duties under the same domain.
## AWS Certificate Manager (ACM)
ACM helps to reduce the complexity of working with these **digital certificates** to secure web traffic. You can use ACM to provision, manage, and deploy TLS certificates for use with AWS services and internally connected resources.
### When should you consider using ACM?

ACM can add value to your operations if you have any of the following use cases:
- To provision and manage TLS certificates for securing web traffic 
- To import existing certificates for use with AWS resources
- To deploy certificates with public-facing web applications on AWS
- To provision and manage private certificates from a private CA if you create them through Amazon Private CA.

![[Pasted image 20251030081142.png]]
You can configure monitoring through services like Amazon CloudWatch to stay aware of certificate-related events and automate responses to those events. If you create a private CA using AWS Private CA, you can use it to issue and manage private certificates through ACM, as well.
### Validating domain ownership with ACM
Before Amazon Trust Services can issue a **public certificate** for your site, ACM must prove you own or control all the domain names you specify in your request. 

You can choose to prove your ownership with either **DNS validation** or **email validation** at the time you request a public certificate.
- For **email validation**, certificate issuers will typically send an email to the contact addresses on file with the registrar for the domain name in the certificate.
- When you choose **DNS validation**, ACM provides you with one or more Canonical Name Records (CNAME) that you must add to the DNS provider's database. These records contain a unique key-value pair that serves as proof that you control the domain.
In general, AWS recommends using DNS validation over email validation for requesting certificates from ACM.
## What is Private CA?
Managing PKI is another cumbersome task often placed upon security teams. Architecting certificate authorities for reliability, designing security controls
With AWS Private CA, you can create your own managed private CA hierarchy, including **root** and **subordinate CAs**. When your CA structure is in pla
ce, you can issue private x.509 certificates for internal authentication, code signing, and other objectives that don't require public trust.
AWS Private CA can add value to your operations if you have any of the following use cases:

- To establish a **private** PKI in the AWS Cloud that you intend to use within your organizatio or other trusted group
- To issue **private** x.509 certificates that you customize to meet your organization's needs
When you create a private CA with AWS Private CA, you can use ACM to provision and manage the private certificates issued by your private CA. You can use these certificates with any AWS service that is compatible with ACM.
You can also export them for use with internal IoT devices, virtual private network (VPN).
![[Pasted image 20251030084815.png]]
### Planning your CA hierarchy
When working with ACM, you don't manage the underlying CA infrastructure. However, you are responsible for designing CA infrastructure when working with AWS Private CA, because the PKI is unique to your organization.
When you first create a CA with AWS Private CA, you create a **root certificate authority**.
Organizations will frequently use several branches and tiers for CAs to logically separate responsibilities, isolate risk, and apply security controls appropriate for each tier. For example, a logistics company might have a root CA, which signs **CA certificates** for intermediate human resources and operations CAs.

With proper segmentation, usually the lowest-ranking CAs will issue the **end-entity certificates** to be used with network-facing resources.

## Application Level Encryption
You might consider to achieve **end-to-end** encryption is encrypting your data at the **application level**.
For most workloads, server-side encryption serves as the recommended choice for protecting data while minimizing complexity.
For highly sensitive workloads, encrypting data at the **application level** can help meet regulatory requirements and provide the highest level of protection.
AWS provides application owners with the following three options designed to streamline this process. These options help developers build secure applications without requiring the additional management overhead associated with proper data protection.
- Use the **AWS Encryption SDK** to encrypt all types of data in your applications.
- Use the **AWS Database Encryption SDK** to encrypt and sign database records in your applications.
- Use the **Amazon S3 Encryption Client** if your use case is limited to working with Amazon S3, and you need advanced functionality, like multipart uploads.
### AWS Encryption SDK
The AWS Encryption SDK is an application-level encryption library designed to make it convenient for everyone to encrypt and decrypt data using industry standards and best practices. The AWS Encryption SDK answers the following questions for you:

- Which encryption algorithm should I use?
- How do I generate the encryption key?
- How do I protect the encryption key, and where should I store it?
- How do I ensure that the intended recipient can read my encrypted data?
- How do I use the data keys that AWS KMS returns?
### AWS Database Encryption SDK
The AWS Database Encryption SDK is a set of software libraries that facilitate application-level encryption in your database design. Like the AWS Encryption SDK, this tool is designed to be convenient for developers.
The AWS Database Encryption SDK provides record-level encryption solutions. You can specify which fields are encrypted and which fields are included in the signatures that ensure the authenticity of your data.


## Resources
[Design a CA hierarchy - AWS Private Certificate Authority](https://docs.aws.amazon.com/privateca/latest/userguide/ca-hierarchy.html)
[Java - AWS Database Encryption SDK](https://docs.aws.amazon.com/database-encryption-sdk/latest/devguide/ddb-java.html)
