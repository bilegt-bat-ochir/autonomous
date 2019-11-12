
![](images/general/workshop_logo.png)

# STEP 1: Create your Autonomous database

## Objectives
- Create your first ATP instance 
- Scale up and down CPU/storage
- Prepare the APEX workspace

# Steps
- Open www.oracle.com and click on the icon in red square.

![](./images/step2/0.signin.png)

- You should see "Sign in to Cloud" link

![](./images/step2/0.signin_cont1.png)

- Enter your cloud account name, which you have previously provided during you account creation, for example "mycloudtenancy". Usually you should have received a welcome email with the subject "Get Started Now With Oracle Cloud" and all the login instruction.

![](./images/step2/0.signin_cont2.png)

- Enter your login credentials, such as admin user account with password.

 ![](./images/step2/0.login.PNG)

- On the left hand menu, choose Autonomous Transaction Processing.

  ![](./images/step2/0.login_cont1.png)

- Click on **Create Autonomous Database**

  ![](./images/step2/1.createATP.PNG)
  
- Enter **Display name** and **Database name** to  the database, in this case "Warrior".

  ![](./images/step2/1.createATP-cont1.PNG)
  
- Please choose the **Transaction Processing**, which is optimized the database for daily transactional processing, just like OLTP database.
- For your demo purpose, please also make sure you choose **"Serverless"**.

  ![](./images/step2/1.createATP-cont2.PNG)
  
- Since this is our first time experience with Autonomous database, let's choose **"ALWAYS FREE"** by click in on Radio button.
  
  ![](./images/step2/1.createATP-cont3.PNG)
  
- For experienced users, who have been using Oracle Database 18c for some period, you can choose to enable **19c** in your Autonomous database, but we will skip and don't choose for this lab.

  ![](./images/step2/1.createATP-cont4.PNG)
  
- Provide your database credential for **"ADMIN"** user schema.

  ![](./images/step2/1.createATP-cont5.PNG)

- **License Included** option will automatically enabled, because we have chosen **ALWAYS FREE** for this lab.

  ![](./images/step2/1.createATP-cont6.PNG)
  
- Provisioning your autonomous database will take usually 3-5 minutes, after that you will be able to experience the power of autonomous. Here is the short video of steps:

![](./images/step2/1.createATP.gif)
	
## Configuring auto-scaling
Auto-scaling is a very powerful feature that lets our application handle peaks of traffic, while keeping costs under control at the same time. We will define a minimum number of OCPUs that our ATP will provision and the database will automatically scale up to three times that number, in case the demand arrives.

- Click on Scale Up/Down.

	![](./images/lab100/Scale.png)

- Activate the AUTO SCALING checkbox: once you turn this on, the database will use up to three times the number of original cores to 
  execute its workloads. 
  
	![](./images/lab100/Autoscaling.png)

## Accesing the Performance Hub
The Performance Hub is a great tool to monitor our ATP status and activity. It is accessible from the Service Console.

- Open the Autonomous Database Details page and click on Performance Hub.
	![](./images/lab100/PerfHubAccess.png)

- In the upper part we will see the consumption of resources and waits of our sessions along time. In the lower part, we will be able to check the ASH (Active Session History) analysis, access the SQL Monitoring to analyze individual queries or even submit a session kill command.
	![](./images/lab100/PerfHub.png)

# Prepare the APEX workspace

  - Go to the details of the autonomous database and open the Service Console.

  ![](./images/lab100/open_service_console.png)
  
  - Go to Development and open APEX.
  
  ![](./images/lab100/open_APEX.png)
  
  -  You will see the login page fof APEX Administration Services. Use the ADMIN password that you entered when you provisioned ATP.

  ![](./images/lab100/open_apex_2.png)

  - Follow the instructions to create a new workspace.
  
  ![](./images/lab100/create_workspace_01.png)

  - In this case let's call the workspace and database user "WORKSHOPATP".
    Keep a note of the password as you will need it later.

  ![](./images/lab100/create_workspace_02.png)
  
# Follow-up questions

![](./images/general/juan.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)
