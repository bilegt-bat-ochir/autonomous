![](/images/oci.jpeg)

- [Go back to main](/README.md)

## Objectives
* Understand IAM concepts, 
  - [What is compartment?](#what-is-compartment)
  - [What is group?](#groups)
  - [What is users?](#users)
  - [how do you authorize them using policies?](#real-cool-heading) 
- Create your first compartment
- Create your first groups and users
- Create your policies and attach it to compartment

## Pre-Requisites: Oracle Cloud Account
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
## Knowledge Check: IAM understanding
# What is compartment?

Compartment is tenancy-wide and across regions resource. It is a logical resource used for separating resources from each other based on different needs. Suppose you need to create separate compartments for your application team, database team, and networking teams from each other. Each of them can have different needs and different access level. [Refer to official oracle document](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Tasks/managingcompartments.htm)

When creating a compartment, you must provide a name for it (maximum 100 characters, including letters, numbers, periods, hyphens, and underscores) that is unique within its parent compartment. 
*You can create subcompartments in compartments to create hierarchies that are 6 levels deep.

After creating a compartment, you need to write at least one policy for it, otherwise no one can access to given compartment.

### What is policy? 

### What is group? 

### What is user? 


## Step 1: Login to the your account for the first time

After your cloud account creation, you will receive confirmation email:
![Sign_in_email]( /images/ocilab/1_sign_email.PNG)

Click on the blue "Sign In to Oracle Cloud" button in email, which will take you to login window, then click on the **Sign in** link.

![Sign_in_email]( /images/ocilab/1_sign_in.PNG)

When you sign in to the Console, the dashboard is displayed.

![Sign_in_email]( /images/ocilab/1_sign_in_console.PNG)

You will notice something in address bar. OCI generates region specific login addresses and each tenants should use correct link.
In my case, ap-tokyo-1, which means my region is Japan and data center is in Tokyo. 

*Full list of [OCI regions and data centers](https://docs.cloud.oracle.com/en-us/iaas/Content/General/Concepts/regions.htm)


## Step 2: Create your compartments

## Step 3: Create your user groups

## Step 4: Create your policies

## Step 5: Create your users and add to existing groups
