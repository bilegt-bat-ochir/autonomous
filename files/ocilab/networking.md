[Oracle Cloud Infrastructure Learning materials](https://bilegt-bat-ochir.github.io/)

# Objectives
* [Understand IAM concepts](#knowledge-check-iam-understanding)
  - [What is compartment?](#what-is-compartment)
  - [What is policy?](#what-is-policy)
  - [What is group?](#what-is-group)
  - [What is user?](#what-is-user)
  - [How do you authorize them using policies?](#User-authorization) 
* [Create your first compartment](#step-2-create-your-compartments)
* [Create your first group](#step-3-create-your-user-groups)
* [Create your policies and attach it to compartment](#step-4-create-your-policies)
* [Create some users and add to existing groups](#step-5-create-your-users-and-add-to-existing-groups)


## Pre-Requisites: 
### Create your Oracle Cloud Account
- First of all, you need an Oracle Cloud account. Sign up [here](https://oracle.com/free) to create a free-tier account. 
- Use your Always Free resources as long as you want with no time constraints—subject only to the capacity limits noted. 
- You will receive $300 of free credits good for up to 30 days of Oracle Cloud usage. 
- When your 30-day trial period for the expanded set of services ends you still can continue using Always free services, includes Autonomous Database, Virtual Machines, Block storage, Object storage and Email notification services with no interruption.

Once you are successfully created your cloud account, you will receive a confirmation email from Oracle.
*Note down your OCI account credentials (User, Password, and Tenant) in safe place.*
- To sign in to the Console, you need the following:
  - Tenant, User name and Password
  - URL for the Console: [https://oracle.com](https://oracle.com)
  - Oracle Cloud Infrastructure supports the latest versions of Google Chrome, Firefox and Microsoft Edge.

### Knowledge Check: IAM understanding
#### What is compartment?

Compartment is tenancy-wide and across regions resource. It is a logical resource used for separating resources from each other based on different needs. Suppose you need to create separate compartments for your application team, database team, and networking teams from each other. Each of them can have different needs, different access level and different purpose. [Refer to official oracle document](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Tasks/managingcompartments.htm)

When creating a compartment, you must provide a name for it (maximum 100 characters, including letters, numbers, periods, hyphens, and underscores) that is unique within its parent compartment. 
*You can create subcompartments in compartments to create hierarchies that are 6 levels deep.*

After creating a compartment, you need to write at least one policy for it, otherwise no one can access to given compartment.

#### What is group? 
A collection of users who all need the same type of access to a particular set of resources or compartment. [Refer to official oracle document](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Concepts/overview.htm)

#### What is policy? 
A policy is a document that specifies who can access which Oracle Cloud Infrastructure resources that your company has, and how. A policy simply allows a group  to work in certain ways with specific types of resources  in a particular compartment, according to official document. [Refer to official oracle document](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Concepts/overview.htm)

#### What is user? 
An individual employee or system that needs to manage or use your company's Oracle Cloud Infrastructure resources. Users might need to launch instances, manage remote disks, work with your virtual cloud network, etc. End users of your application are not typically IAM users. Users have one or more IAM credentials. [Refer to official oracle document](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Concepts/overview.htm)

#### Let's see how the different IAM components work together, and basic features of policies.

In following steps, I will create 3 different compartments for 3 different teams. Each team will have delegated access rights and assigned users.



[Back to the Top](#objectives)
