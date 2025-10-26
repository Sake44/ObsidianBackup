## The AWS Well-Architected Framework

AWS introduces the Well-Architected Framework to provide guidance to help cloud architects build secure, resilient and well-performing infrastructure to host their applications.

The documentation for the Well-Architected Framework (see [Well-architected framework](http://docs.aws.amazon.com/wellarchitected/latest/framework)) also presents many key questions customers should review. It is useful to discuss these questions with the other technical team members in your company to make key decisions about your infrastructure and workloads to be hosted at AWS. Each workload to be deployed at AWS should be viewed through the lens of the Well-Architected Framework following these six pillars.

### **Why use the AWS Well-Architected Framework?**

- **Build and deploy faster:** By reducing emergency response and capacity management and by using automation, you can experiment and release value more often.
- **Lower or mitigate risks:** Understand where you have risks in your architecture, and address them before they impact your business and distract your team.
- **Make informed decisions:** Ensure that you have made active architectural decisions that highlight how they might impact your business outcomes.
- **Learn AWS best practices:** Make sure your teams are aware of best practices that we have learned through reviewing thousands of architectures on AWS.
To understand better how much can be useful Well-Architected Framework we could divide it in four hotspots:

#### Design Principles

The AWS Well-Architected Framework lets you review your architectures and provides guidance to improve designs over time.

The AWS Well-Architected Framework provides a set of questions that are based on design principles across six pillars based on years of knowledge on common customer pain points, architectural problems, and oversights.

 The best practices applied to these questions are summarized into **whitepapers called design principles**.
- The **design principles** are organized into six pillars.
- Design principles are **concepts** and ways of thinking that you must consider when designing a workload.
- **Lenses** provide a way for you to consistently measure your architectures against best practices and identify areas for improvement. The AWS Well-Architected Framework Lens is automatically applied when a workload is defined.

#### Six Pillars
The AWS Well-Architected Framework is composed of a set of general design principles and a set of conceptual themes called the six pillars. These are best practices to operate in the cloud based on AWS experience.
- **Operation Excellence**: The ability to run and monitor systems to deliver business value and continually improve supporting processes and procedures.
- **Reliability**: The ability of a workload to perform its intended function correctly and consistently when it’s expected to.
- **Security**: The ability to protect information, systems, and assets while delivering business value through risk assessments and mitigation strategies.
- **Performance efficency**: The ability to use computing resources efficiently to meet system requirements and the ability to maintain that efficiency as demand changes and technologies evolve.
- **Cost optimization**: The ability to run systems to deliver business value at the lowest price point.
- **Sustainability**: The ability to continually improve sustainability impacts by reducing energy consumption and increasing efficiency across all components of a workload.

### Well-Architected Tool
This is a tool AWS provides that can take a look at your workloads, take a look at the things that you've built inside of your account, once they've been up and running.
The AWS WA Tool reviews your workload and provides recommendations based on the six pillars of the AWS Well-Architected Framework.

### Functional vs Non-functional requirements

**_Functional requirements_** - define what a product/system must do and what its features and functions are.

- **Functional requirements** are the primary way that a customer communicates their requirements to the project team.
- **Functional requirements** help to keep project team going in the right direction.
![[Pasted image 20251025181643.png]]

**_Non-functional requirements_**  - describe the general properties of a system.

Typically, a customer has both **_needs_** and **_wants:_**

- After seeing the cost estimate, they may ask to reduce the scope (Usually removing some of the **_non-functional requirements_** reduces the scope).
- A lot of **_non-functional requirements_** can quickly drive up the cost.
-  Insufficient **_non-functional requirements_** may lead to bad user experience.
![[Pasted image 20251025181750.png]]
