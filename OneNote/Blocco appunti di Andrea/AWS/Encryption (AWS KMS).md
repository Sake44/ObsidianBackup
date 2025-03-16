The data generated and transferred within modern applications is generally encrypted in three phases. Often, your goal will be to achieve **end-to-end** encryption, or encryption of data throughout its lifecycle, until it is ultimately stored.   
To achieve this goal, you can encrypt data at the **application level** before it's transferred, or encrypt the data **in transit** and **at rest.**  
In the context of a typical modern web application, data can be encrypted at the following points:
 
- **Application level:** Consider a transaction generated in a user's browser while using a web application. The app owner can use AWS encryption libraries in their application to encrypt the transaction record before it is sent over the public internet.

**In transit:** The app owner could also choose to encrypt the transaction as it is transferred from the client application to their application servers.

- **At rest**: The application servers process the transaction and update a database accordingly. The app owner can encrypt the underlying storage supporting the database to mitigate damage in case of a compromise.
 ![Infographic categorizing AWS offerings by the encryption phase they are designed to support. Details in following paragraph.](Exported%20image%2020250315115753-0.png)

The AWS Encryption SDK, AWS Database Encryption SDK, and Amazon S3 Encryption Client are used to encrypt data at the **application level** before it is sent across networks. AWS Certificate Manager (ACM) and AWS Private Certificate Authority are used to encrypt **data in transit** across networks. AWS Key Management Service (AWS KMS) and AWS CloudHSM are used to encrypt **data at rest** or data stored in persistent locations.

==Asymmetric Encryption==
 
==An encryption scheme is called asymmetric if it uses one key to encrypt data, and a different but mathematically related key to decrypt data====.==
 > ==Symmetric encryption==   
**Symmetric** encryption refers to encryption using algorithms, in which the same key is used to both encrypt and decrypt data. Symmetric encryption requires that all intended message recipients have access to a shared key.

==AWS KMS can help streamline challenges normally associated with managing encryption keys and encrypting== **data at rest** ==in AWS. AWS KMS is primarily designed as a sort of vending machine for keys. It offers a variety of cryptographic operations for the keys it creates, such as using them to decrypt and encrypt data. You can create customer managed keys or use AWS managed keys to encrypt sensitive data stored on AWS without concern for redundancy, availability, or managing hardware.==
 
AWS KMS can add value to your operations if you have any of the following use cases:
 
- To encrypt data at rest stored in the AWS Cloud with over 100 AWS services, such as Amazon EBS or Amazon S3 - To perform as a key encryption key, or **wrapping key,** provider for the AWS Encryption SDK when performing client-side encryption
   

- To digitally sign and verify data using asymmetric key pairs
- To generate and verify message authentication codes (MACs) - To generate random numbers for cryptographic applications
   

**Key policies**
 
A key policy is a resource policy for an AWS KMS key. Key policies are the primary way to control access to AWS KMS keys. Every AWS KMS key must have exactly one key policy. The statements in the key policy determine who has permission to use the AWS KMS key and how they can use it.  
You can use AWS Identity and Access Management (IAM) policies in combination with key policies to administer permissions for using keys. To complete an operation on a key, the key policy must permit the principal to do so without denial from the IAM policies attached to the principal.
 
**Grants**
 
A grant is a policy instrument that provisions permissions for AWS principals to use AWS KMS keys for a variety of actions, ranging from cryptographic operations to viewing the key. Grants are often used for temporary, just-in-time permissions because you can create one, use its permissions, and delete it without changing your key policies or IAM policies.

**Rotating your keys**
 
Cryptographic best practices discourage extensive reuse of keys that encrypt data directly, such as the data keys that other services request from AWS KMS. When 256-bit data keys encrypt massive amounts of data, they can become **exhausted**. The ciphertext produced by an exhausted key will show subtle patterns that clever, malicious actors can exploit to discover the bits in the key.

**What is CloudHSM?**
 
HSMs, or hardware security modules, are computing devices that perform cryptographic operations and provide secure storage for cryptographic keys. Customers might have strict security requirements to maintain control over the HSMs that generate and store their encryption keys.
   

**When should you consider using CloudHSM?**
 
CloudHSM can add value to your operations if you have any of the following use cases:
 
- To provision and manage the HSMs that generate and store your encryption keys
- To implement encryption instead of AWS KMS, if your applications don't support API calls
- To configure SSL offloading by reducing the cryptographic workload on your web servers
- To store the Transparent Data Encryption (TDE) key for your Oracle databases

![File is sent with a signature to help ensure data integrity. Details in text.](Exported%20image%2020250315115754-1.png)