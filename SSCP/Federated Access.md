**Federated access, also known as federated identify management (FIM), enables users from one organization to securely access resources or services hosted by another organization without the need for separate authentication credentials.**  
==Instead of maintaining separate user accounts and authentication mechanisms for each system, federated access allows the use of their existing credentials from their home organization to access resources located in external organizations.==  
==There are three central entities in FIM:==

- _Clients or principals._ ==These are the end users interacting with various systems and services to access resources and applications across different organizations. End users authenticate themselves to the identity provider (IdP) and are then granted access to resources by service providers (SPs) based on the authentication assertions provided by the IdP.==
- _Service providers or relying parties (RPs)._ ==SPs provide services or resources that end users need to access. The SPs rely on the authentication and authorization information provided by the IdPs to determine whether to grant users access to specific resources or functionalities.== 
- _IdP._ ==The IdP is the system responsible for managing and verifying the identity of users and providing authentication services to other systems or applications. Its primary function within FIM is to authenticate users and issue security tokens that contain information about the authenticated user. These security tokens are then used by the service providers, or RPs, to grant access to resources or services.==

![Exported image](Exported%20image%2020250315115818-0.png)

**The IdP will use standard authentication protocols such as the Security Assertion Markup Language (SAML), OpenID Connect (OIDC), or Open Authorization 2.0 (OAuth 2.0) to communicate with RPs and exchange authentication information securely.**  
==By centralizing authentication and identity management, IdPs simplify the user experience (users must only sign in once), enhance security, and streamline access control across distributed systems and applications.==

- _SAML._ ==SAML is an XML-based standard for exchanging authentication and authorization data between IdPs and service providers. It allows for single sign-on (SSO) capabilities, where users can log in once to access multiple applications or services.== 
- _OAuth 2.0._ ==As stated, OAuth 2.0 is an authorization framework that allows third-party applications to access resources on behalf of a user without needing to know the user’s credentials. While OAuth focuses on authorization, it is often used with OpenID Connect for authentication purposes.==
- _OIDC._ ==You will recall that it is an authentication protocol built on top of OAuth 2.0, providing identity layer functionalities. It allows clients (RPs) to verify the identity of end users based on authentication performed by IdPs. OIDC enables SSO and identity federation across different domains.==