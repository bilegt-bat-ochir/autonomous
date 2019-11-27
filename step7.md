- [Go back to main](/README.md)
- [Go back to previous step](/step6.md)

# Step 7: Access REST service from APEX
## Objectives
- Create your second workspace with an empty application
- Utilize RESTful service using GET,POST,PUT,DELETE methods from the second workspace RESTATP.

## Create your second workspace with an empty application.

-  You will follow same steps as we did in [step 4](step4.md). Logout from your current APEX workspace, and login as **ADMIN** user. When you are logging as **ADMIN** user, name of the workspace is **INTERNAL** and password is your database password which you have provided in ATP instance provisioning.

  ![](./images/step6/2.websource.PNG)

- Click on **Create workspace** to configure your second APEX workspace. Let's name it **RESTATP** and remember *keep note of the password as you will need it later.*
  
  ![](./images/step6/2.websource-cont1.PNG)
  
- New workspace and database user is created. Now click on hyperlink "RESTATP".

  ![](./images/step6/2.websource-cont2.PNG)
  
- Provide your password when you created "RESTATP" user in previous step.

  ![](./images/step6/2.websource-cont2_1.PNG)

- Go to App Builder and click on **Create Application**, then choose New Application from the options. 
- We will create an empty application, therefore just provide the name then click **Create Application**.

  ![](./images/step6/3.rest.PNG)

- Explore your new application.

## Configure RESTful web source.
- Now we will create our RESTful web source in our newly created application. Go to your application then open **Shared Components**.

  ![](./images/step6/3.rest-cont1.PNG)  
  
- Find **Web Source Modules** from Data Sources section.

  ![](./images/step6/3.rest-cont2.PNG)  
  
- You have some options here when dialog pops up, but since this is our first web source, we go with the first option.

  ![](./images/step6/3.rest-cont3.PNG)  
  
- Choose **Oracle REST Data Services**, provide a name, and paste the full URL of your REST service from the previous step.

  ![](./images/step6/3.rest-cont4.PNG)  
  
- Click Next

  ![](./images/step6/3.rest-cont5.PNG)  
  
- If web source works, it will show you some result. Click on **Create Web Source**.

  ![](./images/step6/3.rest-cont6.PNG)  
  
- Now you should be seeing your web source and successfull message, click on new web source and review what it can do.

  ![](./images/step6/3.rest-cont7.PNG)  
  
- Notice, only GET and POST operations have been added. Click on **Add Operation**

  ![](./images/step6/3.rest-cont7_1.PNG)  

- We will add 3 more operations GET, PUT, DELETE with variable :cust_id, as shown in below one by one.

  ![](./images/step6/3.rest-cont7_2.PNG)  
  
- Make sure you save your work after adding each operation:

  ![](./images/step6/3.rest-cont7_6.PNG)

- You should have now 5 operations available for your REST web source.

  ![](./images/step6/3.rest-cont7_5.PNG)  

- Save your web source.

  ![](./images/step6/3.rest-cont7_6.PNG)  

- Now let's test it by adding a Report page with some forms. Go back to your application and **Create a Page**.

  ![](./images/step6/3.rest-cont8.PNG)  

- Choose **Report with Form** and click Next

  ![](./images/step6/3.rest-cont8_1.PNG)  

- Provide report page name and form page name as below

  ![](./images/step6/3.rest-cont8_2.PNG)  

- You can create a navigation menu

  ![](./images/step6/3.rest-cont8_3.PNG)  

- Now we need to choose **Web Source** and find your previously created module, then click Next

  ![](./images/step6/3.rest-cont8_4.PNG)  

- Choose primary key column as **CUST_ID** column and create your page.

  ![](./images/step6/3.rest-cont8_5.PNG)  

- Run your application

  ![](./images/step6/3.rest-cont9.PNG)  

- You will see a grid with full of data which are retrieved from **WORKSHOPATP** using RESTful service.

  ![](./images/step6/3.rest-cont9_1.PNG)  

- This concludes the generic idea of Autonomous database and oracle REST data service. Autonomous Database includes native APEX support, you cano use the RESTful Services development pages in APEX to build and maintain your services and REST enabled objects. 
- However you can connect almost any service to your Autonomous Database. Enjoy!

## You may continue to next step 
- [Machine Learning features in Autonomous Database](/step8.md)

## Follow-up questions

![](./images/bilegt.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)
