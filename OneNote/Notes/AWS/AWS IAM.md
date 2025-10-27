**Authentication answers the question, "Are you who you say you are?" Authorization answers the question, "What actions can you perform?"**

When you create your AWS account, you use the combination of an email address and a password to verify your identity. If a user types in the correct email address and password, the system assumes the user is allowed to enter and grants them access. This is the process of authentication.  
After you’re authenticated and in your AWS account, you might be curious about what actions you can take. This is where authorization comes in. Authorization is the process of giving users permission to access AWS resources and services.   
AWS Identity and Access Management (IAM) is an AWS service that helps you manage access to your AWS account and resources. It also provides a centralized view of who and what are allowed inside your AWS account (authentication), and who and what have permissions to use and work with your AWS resources (authorization).
 ![Exported image](Exported%20image%2020250315115710-0.png)  

**IAM Roles and Services**  
[https://docs.aws.amazon.com/en_us/IAM/latest/UserGuide/id.html](https://docs.aws.amazon.com/en_us/IAM/latest/UserGuide/id.html)  
Some AWS services will need to perform actions on your behalf. To do so we will assign permissions to AWS services with **IAM roles.**  
A role is an identity you can create in IAM that has specific permissions. A role is similar to a user, as it is an AWS identity with permission policies that determine what identity can and cannot do in AWS. A role is intended to be assumable by anyone who needs it so it's not associated with one person.  
As security tools IAM provide a Credential Report (account-level) and Access Advisor (user-level).  
The reason why we use roles instead of credentials is that if our web server get hacked they can access to our credentials stored in a file. In this way they can read our Access Key and Private Access Key and able to log in our s3 account. Using roles is so much more secure cause you not store credentials in your ec2 instance.
 
**AWS IAM Guidelines &  Best Practices**

1. Don't use root account except for AWS account setup
2. One physical user = One AWS User
3. Assign user to groups and assign permission to group
4. Create a strong password policy
5. Use an enforce the use of MFA
6. Create and use Roles for giving permissions to AWS Services
7. Use Access Keys for Programmatic Access (CLI/SDK)
8. Audit permissions of your account using IAM Credentials Report & IAM Access Advisor
9. NEVER share IAM users & Access Keys

**Main Topics:**

![Exported image](Exported%20image%2020250315115710-1.png)  

**User Groups:**  
An IAM group is a collection of users. All users in the group inherit the permissions assigned to the group. This makes it possible to give permissions to multiple users at once. It’s a more convenient and scalable way of managing permissions for users in your AWS account. This is why using IAM groups is a best practice.

**IAM policy examples**  
Most policies are stored in AWS as JSON documents with several policy elements. The following example provides admin access through an IAM identity-based policy.
 
This policy has four major JSON elements: **Version**, **Effect**, **Action**, and **Resource**.

- The **Version** element defines the version of the policy language. It specifies the language syntax rules that are needed by AWS to process a policy. To use all the available policy features, include **"Version": "2012-10-17"** before the **"Statement"** element in your policies.
- The **Effect** element specifies whether the policy will allow or deny access. In this policy, the Effect is **"Allow"**, which means you’re providing access to a particular resource.
- The **Action** element describes the type of action that should be allowed or denied. In the example policy, the action is **"*"**. This is called a wildcard, and it is used to symbolize every action inside your AWS account.
- The **Resource** element specifies the object or objects that the policy statement covers. In the policy example, the resource is the wildcard **"*"**. This represents all resources inside your AWS console.