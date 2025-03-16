- **Identity Management Life Cycle**==: This includes five areas:== **provisioning, proofing, authorization, maintenance, and entitlement.**
- **Provisioning**==: The process of creating and managing identities, which involves:==
    
    - ==Creating identifiers==
    - ==Linking to authentication providers==
    - ==Setting attributes and privileges==
    - ==Decommissioning identities==
- **Forms of Provisioning**==:==
    
    - **Manual Provisioning**==: Handled by administrators for human users.==
    - **Self-Provisioning**==: Allows users to manage their own identity parameters.==
    - **Just-in-Time Provisioning**==: Enables immediate identity creation and access.==
- **Identity Assurance Levels (IAL)**==: Ranges from IAL 1 (no validation) to IAL 3 (physical document verification).==
- **Identity Proofing**==: Verifies identities before account issuance, involving resolution, validation, and verification steps.==
- **Identification**==: Establishes unique identifiers for users, which can include user IDs, biometrics, and device authentication.==

**Authorization**  
**Authorization describes what actions or resources authenticated entities can access based on their identity and assigned permissions.**
 
Authorization can be managed through controls based on user roles, user or resource attributes, and policies. An identity and access management (IAM) policy store can be used to hold the authorization policies and compare them to the entity’s access request.
 
**Least Privilege**  
==Authorization is where the principles of least privilege and need to know apply. These principles both have a common theme, although they are slightly different. Least privilege grants a person only the minimum level of access required for them to perform their job function—perhaps read-only or guest-level access. Need to know is a step beyond that; not only must a user have a least privilege level of access, but the user must also need to know a specific set of information within that least privilege level of access. We most typically find need to know in the military world, where least privilege can translate to a user’s clearance level.==
 
**Separation of Duties**  
==A core element of authorization is the principle of separation of duties, also known as segregation of duties. Separation of duties is based on the security practice that no one person should control an entire high-risk transaction from start to finish. Separation of duties breaks the transaction into separate parts and requires that no one person be allowed to execute all parts of the transaction.== 
    
**Identity Proofing**  
**Identity proofing, also known as identity verification or identity authentication, is the process of confirming that an individual’s claimed identity is valid and accurate.**  
Identity proofing involves verifying that a person is who they claim to be, typically during the initial enrolment or registration process.  
**Identity proofing is crucial for establishing trust and ensuring the integrity of identity-related transactions, particularly when an absence of physical presence makes it easier to impersonate others.**  
Proofing can be done up to the level of different identity assurance levels (IALs).
 
- IAL1 represents the lowest level of assurance in identity proofing.
- IAL2 requires identity proofing using an online identity authentication service, which can be done with services like social media systems.
- IAL3, the highest level of identity assurance, can be achieved through rigorous identity proofing and verification process.

**Provisioning**  
**Provisioning an identity involves creating, managing, and maintaining user accounts and access rights within an organization’s IT systems and applications.**
 3. _User onboarding request._ ==The process starts with a user onboarding request, initiated by a new employee, a manager, or an authorized administrator. This request may include details such as the user’s name, job title, department, and required access permissions.==
4. _User identity verification._ ==Before provisioning an identity, the organization verifies the identity of the user by confirming their identity through inspection of official documentation.==
5. _Account creation._ ==Once the user’s identity is verified, an account is created for them in the organization’s identity management system (e.g., Active Directory, Lightweight Directory Access Protocol). This involves assigning a unique username, generating a password==
6. ==Access permissions assignment. Access permissions are assigned to the user based on their job role, department, or specific requirements. This includes granting permissions to access systems, applications, databases==
7. _Access approval and review._ ==Access permissions are reviewed and approved by the user’s manager or an authorized administrator to ensure that they align with business requirements and security policies. This step helps prevent unauthorized access and ensures that users have the necessary access to perform their job duties.==
8. _Account provisioning._ ==The user account and access permissions are provisioned to the relevant systems and applications within the organization’s IT infrastructure.==
9. _User notification._ ==Once the user account is provisioned, the user is notified of their account credentials, access permissions, and any additional information or instructions relevant to their role. This may include guidance on security best practices, password policies, and instructions for accessing resources.==
10. _Ongoing management and maintenance._ ==The identity provisioning process is not a one-time event but an ongoing activity that requires regular maintenance and updates.==
 
**Deprovisioning**  
**Deprovisioning involves revoking access rights and disabling user accounts for individuals who no longer require access to an organization’s systems, applications, or resources.**

**Monitoring, Reporting, and Maintenance**  
**The maintenance stage of the identity and access management (IAM) life cycle involves ongoing monitoring, reporting, and maintenance of user identities, access rights, and security controls.**
 
**Role Changes**

- **Identification of role changes**_._ ==Organizations identify role changes that occur due to employee promotions, transfers, demotions, or changes in job responsibilities.== 
- **Access review and adjustment**_._ ==Access permissions associated with the user’s previous role are reviewed and, ideally, completely removed or “torn down,” and then built-up, or provisioned in accordance with the user’s new role.== 
- **Role-based access control (RBAC)** _updates._ ==RBAC policies are updated to reflect changes in organizational roles and responsibilities.==
- **Notification and communication**_._ ==Stakeholders, including human resources, IT administrators, managers, and the user, are notified of role changes and any actions required to smoothly transition access rights or responsibilities.==         
          
**Entitlement**  
**In an identity and access management (IAM) system, the term “entitlement” refers to the specific access permissions or rights granted to a user or group of users within an organization’s digital environment.**
 
Entitlements dictate what resources, applications, data, or services a user is authorized to access and what actions they can perform once authenticated. Entitlements play a crucial role in IAM systems by ensuring users have appropriate access to resources and services while maintaining security and compliance with organizational policies and regulations.
   

**Entitlements and Inherited Rights**  
==Inherited rights—also known as role-based inheritance or role-based access control (RBAC) inheritance—refer to the mechanism by which users inherit entitlements based on their membership in predefined roles or groups.==