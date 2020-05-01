- [Go back to main](AutonomousWorkshop.md)
- [Go back to previous step](step2.md)

# STEP 3: Explore Autonomous Database console #
## Objectives

- Scale up/down your ATP
- Configure auto-scaling
- Accessing to performance hub
- Move your resource to different compartment

## Scale up and down your ATP

- Open you ATP instance and you can scale up, down your compute power, storage size by clicking on Scale Up/Down.

	![](/images/lab1/step3/1.scaleup.PNG)

- Enter 4 OCPU in compute and 2TB in storage values
  
	![](/images/lab1/step3/1.scaleup-cont1.PNG)
	
## Configure auto-Scaling in your ATP

Auto-scaling is a very powerful feature that lets our application handle peaks of traffic, while keeping costs under control at the same time. We will define a minimum number of OCPUs that our ATP will provision and the database will automatically scale up to three times that number, in case the demand arrives.

- Click on Scale Up/Down.

	![](/images/lab1/step3/1.scaleup.PNG)

- Activate the AUTO SCALING checkbox: once you turn this on, the database will use up to three times the number of original cores to 
  execute its workloads. 
  
	![](/images/lab1/step3/1.scaleup-cont2.PNG)

## Accesing the Performance Hub
The Performance Hub is a great tool to monitor our ATP status and activity. It is accessible from the Service Console.

- Open the Autonomous Database Details page and click on Performance Hub.
	![](/images/lab1/step3/2.performancehub_1.PNG)

- In the upper part we will see the consumption of resources and waits of our sessions along time. In the lower part, we will be able to check the ASH (Active Session History) analysis, access the SQL Monitoring to analyze individual queries or even submit a session kill command.
	![](/images/lab1/step3/2.performancehub.PNG)

## Here is the short summary video of above steps:

  ![](/images/lab1/step3/1.scaleup.gif)

# Additional steps
## Move your resource to different compartment

To move resources between compartments, resource users must have sufficient access permissions on the compartment that the resource is being moved to, as well as the current compartment

- In the list of Autonomous Databases, click on the display name of the database you wish to move, then click on Actions

	![](/images/lab1/step3/3.moveresource.PNG)

- Click move resource and choose the new compartment of your ATP.

	![](/images/lab1/step3/3.moveresource-cont1.png)
	
## Start/stop/terminate your autonomous database

**Stopping your database has the following consequences:**
- On-going transactions are rolled back.
- CPU billing is halted based on full-hour cycles of usage.
- You will not be able to connect to your database using database clients or tools.

Go to Actions, and then click Stop (or Start). When you stop your Autonomous Database, billing stops for CPU usage. Billing for storage continues when the database is stopped.

- In the list of Autonomous Databases, click on the display name of the database you wish to stop, then click on Stop

	![](/images/lab1/step3/4.manage.PNG)

- Check the status, confirm that your Autonomous database is **stopped**.
	
	![](/images/lab1/step3/4.manage-cont1.PNG)

- Find the database you wish to start, then click on Start

	![](/images/lab1/step3/4.manage-cont2.PNG)

- Check the status, confirm that your Autonomous database is **started** successfully.
	
	![](/images/lab1/step3/4.manage-cont3.PNG)
	
- Terminating an Autonomous Database permanently deletes it. The database data, including automatic backups, will be lost when the system is terminated. Manual backups remain in Object Storage and are not automatically deleted when you terminate an Autonomous Database. *Oracle recommends that you create a manual backup prior to terminating.
- In the list of Autonomous Databases, click on the display name of the database you wish to administer then click terminate.
	
	![](/images/lab1/step3/4.manage-cont4.PNG)

- Confirm that you wish to terminate your Autonomous Database in the confirmation dialog by providing database name.
	
	![](/images/lab1/step3/4.manage-cont5.PNG)
	
- Check and confirm, status is now **TERMINATED**.
	
	![](/images/lab1/step3/4.manage-cont6.PNG)
	
## You may continue to next step 
- [APEX on Autonomous Database](step4.md)

## Follow-up questions

![](/images/bilegt.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)
