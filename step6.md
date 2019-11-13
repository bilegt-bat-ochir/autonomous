- [Go back to main](/README.md)
- [Go back to previous step](/step5.md)

# Step 6: REST in APEX
## Objectives
- Define RESTful services in Autonomous database.
- Create an app in a second workspace RESTATP.
- Utilize RESTful service using GET,POST,PUT,DELETE methods from the second workspace RESTATP.

What is REST(Representational State Transfer), It's an architecture that provides interoperability between two computer systems using HTTP(s) protocol as a transport protocol.
Content usually represented via **JSON** or **XML** and great thing about REST is the two participants in the communication can be completely different in terms of:
  - Language (JAVA,.NET, PHP, etc.)
  - Database (Oracle, Microsoft, MongoDB, Hadoop, Couchbase, etc.)
  - Architecture (On Premises, Cloud, Mixed)
  
 ![](./images/step6/0.rest.png)


We will learn just how easy it is to build Oracle APEX apps utilizing RESTful Services.

## Define RESTful services in Autonomous database.

In this part we will enable REST services in WORKSHOPATP instance.
- Go to your APEX workspace

  ![](./images/step4/1.apex-cont6.PNG)
  
- Open SQL Workshop, this is built-in, web edition of Oracle SQL developer, and can fulfill the most of your needs. Go to RESTful services tab.

  ![](./images/step6/1.sqldev.PNG)
  
- As you can see, currently there is no schema is enabled for REST.
  ![](./images/step6/1.sqldev-cont1.PNG)
- Go to SQL commands tab and run following code. 

```
BEGIN
     ords.enable_schema (
         p_enabled               => TRUE,
         p_schema                => 'WORKSHOPATP',
         p_url_mapping_type      => 'BASE_PATH',
         p_url_mapping_pattern   => 'workshopatp',
         p_auto_rest_auth        => TRUE
     );
     COMMIT;
END;
```
  
  Result as below:
  
  ![](./images/step6/1.sqldev-cont2.PNG)

- Go back to RESTful services tab, now you can see the differences. We have enabled REST services in **WORKSHOPATP** schema.

  ![](./images/step6/1.sqldev-cont3.PNG)
  
## Here is the short summary video of above steps:



## You may continue to next step 
- [REST in APEX](README.md)

## Follow-up questions

![](./images/bilegt.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)
