![](/images/oci.jpeg)

- [Go back to main](/README.md)

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

#### Step 1: Login to the your account for the first time

After your cloud account creation, you will receive confirmation email:
![Sign_in_email]( /images/ocilab/1_sign_email.PNG)

Click on the blue "Sign In to Oracle Cloud" button in email, which will take you to login window, then click on the **Sign in** link.

![Sign_in_email]( /images/ocilab/1_sign_in.PNG)

When you sign in to the Console, the dashboard is displayed.

![Sign_in_email]( /images/ocilab/1_sign_in_console.PNG)

You will notice something in address bar. OCI generates region specific login addresses and each tenants should use correct link.
In my case, ap-tokyo-1, which means my region is Japan and data center is in Tokyo. 

*Full list of [OCI regions and data centers](https://docs.cloud.oracle.com/en-us/iaas/Content/General/Concepts/regions.htm) can be found here*

#### Step 2: Create your compartments
As I said in knowledge check, it is logical separation for resources to isolate from each other. I am going to create Network, Application and Database compartments. By default, a root compartment was created for you when you created your cloud account, and of course it is possible to create everything in the root compartment. I would not do that, also Oracle recommends that you create sub-compartments to help manage your resources more efficiently.

From the left top hamburger menu, hover on **Identity** and select **Compartments**.  
![Create a compartment](/images/ocilab/2_compartments.png)

Click on the blue **Create Compartment** button to create a sub-compartment.

![Create a compartment](/images/ocilab/2_compartments_create.PNG)

I am going to create 3 different compartments to isolate cloud resources from each other. Name your compartment, give good description for future reference, and choose parent compartment. You can also add cost-tracking tagging in OCI resources. I am going to add my user name for instance.

Application compartment
![Create a compartment](/images/ocilab/2_compartments_create_app.PNG)

Database compartment
![Create a compartment](/images/ocilab/2_compartments_create_database.PNG)

Network compartment
![Create a compartment](/images/ocilab/2_compartments_create_network.PNG)

We created 3 compartments under root compartment. 
*If you want to delete a compartment, note it must be empty.*

#### Step 3: Create your user groups
Now let's create some groups and later we will write some policies for them as permissions.

From the left top hamburger menu, hover on **Identity**, then select **Groups**.

![Create Group](/images/ocilab/3_groups_create.PNG)

Similar to compartment, you need name it meaningful and give good description for future references.

A group for my application team
![Create Group](/images/ocilab/3_groups_create_app.PNG)

A group for my database admins
![Create Group](/images/ocilab/3_groups_create_database.PNG)

A group for my network division
![Create Group](/images/ocilab/3_groups_create_network.PNG)

#### Step 4: Create your policies
We grant resource permissions to certain groups and users by writing some policies. With right set of policies you will have good governance in your cloud tenancy. 
I strongly suggest you to review and [refer to official oracle document](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Concepts/overview.htm) 

Click on left top hamburger menu, hover on **Identity**, then select **Policies**
![Create Policy](/images/ocilab/4_policies_create.PNG)

Click on the blue **Create Policy** button to create some polices for AppTeam in root compartment.

![Create Policy](/images/ocilab/4_policies_create_app.PNG)
* Enter following policy statements for App_team. 

| **Statement**                                                             | **Explanation** | 
| ---------------------------------------------------------------------------|----------------- |
| Allow group App_team to manage instance-family in compartment Application | Grant to do everything with instances in Application compartment|
| Allow group App_team to manage volume-family in compartment Application | Grant to attach/detach any existing volumes that already exist in compartment Application |
| Allow group App_team to use virtual-network-family in tenancy | Grant to use network resources in tenancy level, it can be changed to compartment level |
| Allow group App_team to read app-catalog-listing in tenancy | Grant to list OCI marketplace images |

![Create Policy](/images/ocilab/4_policies_create_database.PNG)
![Create Policy](/images/ocilab/4_policies_create_network.PNG)

#### Step 5: Create your users and add to existing groups
