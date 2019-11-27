- [Go back to main](/README.md)
- [Go back to previous step](/step9.md)

# Step 10: Load data into Autonomous database

You can load data into Autonomous Database using Oracle Database tools and 3rd party data integration tools. Data can be loaded:
- From files local to your client computer
- From files stored in a cloud-based object store

For the fastest data loading experience Oracle recommends uploading the source files to a cloud-based object store before loading the data into your Autonomous Database.

We will use the PL/SQL package **DBMS_CLOUD**. The DBMS_CLOUD package supports loading data files from the following Cloud sources: 

1. Oracle Cloud Infrastructure Object Storage (OCI Object Storage)
2. Oracle Cloud Infrastructure Object Storage Classic
3. Amazon AWS S3

This tutorial shows how to load data from OCI Object storage using two of the procedures in the DBMS_CLOUD package:
* `create_credential`: Stores the object store credentials in your Autonomous Database schema.
* `copy_data`: Loads the specified source file to a table. 

**Pre-requisites**

* Completion of [Step 2](/step2.md)
* A bucket in OCI Object storage
* Authentication token of your user

## Load a data file to your Object Store ##

The first thing is first, you need to upload your dump file to somewhere, but I prefer to upload to Oracle object storage, which is incredibly cheap and way to easy to access. Because OCI offers two distinct storage class tiers. 
Object Storage, for data which you need fast, immediate and frequent access and Archive Storage, for data which you seldom or rarely access.

- Login to your Oracle Cloud Infrastructure Console

- Select **Object Storage** -> **Object Storage** from the drop down menu on the top left of the Oracle Cloud Infrastructure console.

![](/images/step10/0.objectstorage.png)

- Select **Create Bucket** to create a bucket to load your data in. 

 ![](/images/step10/0.objectstorage-cont1.png)

- Click on the bucket name you just created. [Download sample files](./files/datafiles_for_sh_tables.zip) and extract to your local storage, then upload everything to your newly created bucket 

 ![](/images/step10/0.objectstorage-cont2.png)
 
- The final step will be to change the visibility of your bucket. Click the **Edit Visibility** button at the top of your Bucket Details screen.

  ![](/images/step10/0.objectstorage-cont3.png)

Change the visibility to **Public**, accept all other defaults.  Click **Save Changes**. Your bucket should now be visible and public.  Verify and proceed to setting up your Auth token.

## Create an Object Store Auth Token ##

To load data from the OCI object store, you need to create an Auth Token for your object store account. The communication between your Autonomous Database and the object store relies on this Auth Token and username/password authentication.

- Go to your Identity console, choose from the menu on the top left select **Identity->Users**. Once on the Users Page click on your username. Click **Auth Tokens** under **Resources** on the left of the console, then click **Generate token**.

*Copy the generated token to notepad located on your desktop. The token does not appear again and you WILL NEED this token to load your data into ADW.*

  ![](/images/step10/1.token.PNG)
    
## Create Object Store Credentials in your Autonomous Database ##

Now that you have created an object store Auth Token, its time to store the credentials of the object store in ADW instance.

- Let's navigate to SQL Developer web to prepare your ADW instance for the staged data. Go back to your ADW instance via the menu.

  ![](/images/step10/2.loading.PNG)
- Enter your database admin username from the previous steps and login to your Autonomous instance. 
  
  ![](/images/step10/2.loading-cont1.PNG)

- SQL Developer Web has an interface similar to the installed client. Note where the Worksheet is and the Query Results. Copy the below PL/SQL script. Modify it by your need, 
1. Credential name, give meaningful
2. Username
2. Password is the authentication token

```
BEGIN
    DBMS_CLOUD.CREATE_CREDENTIAL(
    credential_name => 'BucketCredential',
    username => 'oracleidentitycloudservice/bilegt.bat.ochir@oracle.com',
    password => 'your token is here');
    END;
/
```
Press the green arrow to run the worksheet.  Once the correct information is entered, you should get a message that the PL/SQL procedure completed. Your object store's credentials are stored in your ADW instance now.  
  ![](/images/step10/2.loading-cont2.PNG)

## Copy Data from Object Store to Autonomous Database Tables ##
Before data is copied, the tables and objects need to be created in ADW.  In this lab you will create the target objects. [Download sql script](./files/create-table-script.sql) and paste the commands in your SQL Developer Web worksheet.

  ![](/images/step10/2.loading-cont3.PNG)

*Once the script has run review the output to ensure the tables and constraints have been created successfully.*

- Now you have empty tables and staged data in the OCI Object store. To get the data from the object store to your ADB instance, you need to get some information about the object. To move the data we will be using the dbms_cloud.copy_data procedure. The procedure takes information about the location of the data you staged in your object store.  Review the procedure.

    ```
    SQL    
    begin
    dbms_cloud.copy_data(
        table_name =>'<ENTER_TABLE_NAME>',
        credential_name =>'BucketCredential',
        file_uri_list =>'<entertenancy-bucket-address>/chan_v3.dat',
        format => json_object('ignoremissingcolumns' value 'true', 'removequotes' value 'true')
    );
    end;
    /
    ```
- Download this [sql script](./files/load-data-script.sql) to load your tables. 

  ![](/images/step10/2.loading-cont4.PNG)

*In the Script Output, once you see the message PL/SQL procedure successfully completed. Query a few of the tables to see the rows that were inserted.*

- You can check each table's data and number of rows 

```
SELECT * FROM ADMIN.SALES;
SELECT COUNT(1) FROM ADMIN.SALES;
```

Success! Notice that the data has been copied from the object store to the tables in your ADW instance. This can be done for multiple tables providing an easy migration path from your existing databaset to Autonomous Database.


### You may continue to next step 
- [More coming](README.md)
- [This file](/files/ATP-Hands-on-Lab.pdf) is maybe outdated, but I'd suggest you to try at least Node.js and Python parts. Also, there are tonnes of documents and github pages to help you for your Autonomous Journey :) 
- I will be adding more contents to this page, maybe it's good idea to bookmark this page. Thank you.

## Follow-up questions

![](./images/bilegt.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)

