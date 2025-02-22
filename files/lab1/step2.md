- [Go back to main](AutonomousWorkshop.md)
- [Go back to previous step](step1.md)

![](/images/welcome.jpeg)

# STEP 2: Create your Autonomous database

## Objectives
- Create your first ATP instance
- Create your ALWAYS FREE autonomous database instance

## Create your first ATP instance
- Open www.oracle.com and click on the icon in red square.

![](/images/lab1/step2/0.signin.png)

- You should see "Sign in to Cloud" link

![](/images/lab1/step2/0.signin_cont1.png)

- Enter your cloud account name, which you have previously provided during you account creation, for example "mycloudtenancy". Usually you should have received a welcome email with the subject "Get Started Now With Oracle Cloud" and all the login instruction.

![](/images/lab1/step2/0.signin_cont2.png)

- Enter your login credentials, such as admin user account with password.

 ![](/images/lab1/step2/0.login.PNG)

- On the left hand menu, choose Autonomous Transaction Processing.

  ![](/images/lab1/step2/0.login_cont1.png)

- Click on **Create Autonomous Database**

  ![](/images/lab1/step2/1.createATP.PNG)
  
- Enter **Display name** and **Database name** to  the database, in this case "Warrior".

  ![](/images/lab1/step2/1.createATP-cont1.PNG)
  
- Please choose the **Transaction Processing**, which is optimized the database for daily transactional processing, just like OLTP database.
- For your demo purpose, please also make sure you choose **"Serverless"**.

  ![](/images/lab1/step2/1.createATP-cont2.PNG)
  
- Choose OCPU count **1** and storage size **1TB** for this lab.
  
  ![](/images/lab1/step2/1.createATP-cont3.PNG)
  
- For experienced users, who have been using Oracle Database 18c for some period, you can choose to enable **19c** in your Autonomous database, but we will skip and don't choose for this lab.

  ![](/images/lab1/step2/1.createATP-cont4.PNG)
  
- Provide your database credential for **"ADMIN"** user schema.

  ![](/images/lab1/step2/1.createATP-cont5.PNG)

- If you have license you can choose **BYOL** option, or if you don't have appropriate license and you wish to get one choose **License Included**

  ![](/images/lab1/step2/1.createATP-cont6.PNG)
  
- Provisioning your autonomous database will take usually 3-5 minutes, after that you will be able to experience the power of autonomous. 
## Create your **ALWAYS FREE** autonomous database instance

- You need to follow same steps as previous, however, in order to have your **ALWAYS FREE** autonomous database, by clicking on radio button as shown in below 

  ![](/images/lab1/step2/1.createATP-cont3_2.PNG)
  
- Once you click on radio button **ALWAYS FREE**, compute power and storage will be limited by default, you cannot edit the values.

  ![](/images/lab1/step2/1.createATP-cont3_3.PNG)

- **License Included** option will automatically enabled when you choose to enable **ALWAYS FREE**.

  ![](/images/lab1/step2/1.createATP-cont3_4.PNG)

## Here is the short summary video of provisioning ATP instance:

  ![](/images/lab1/step2/1.createATP.gif)

Now you have two autonomous databases, **Autonomous Transaction Processing** and **ALWAYS FREE ATP**.

## You may continue to next step 
- [Explore Autonomous database console](step3.md)


## Follow-up questions

![](/images/bilegt.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)
