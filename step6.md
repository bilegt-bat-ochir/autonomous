- [Go back to main](/README.md)
- [Go back to previous step](/step5.md)

# Step 6: REST in APEX
## Objectives
- Define RESTful services in Autonomous database.
- Create your second workspace RESTATP and create an empty application.

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

- Go back to RESTful services tab, now you can see the differences. We have enabled REST services in **WORKSHOPATP** schema. But there is no object is accessible.

  ![](./images/step6/1.sqldev-cont3.PNG)

- Go to SQL Commands tab and run following code. 

```

begin
    ords.delete_module(
        p_module_name => 'customers.rest' );
    ords.define_module(
        p_module_name => 'customers.rest',
        p_base_path => '/customers/' );
    ords.define_template(
        p_module_name => 'customers.rest',
        p_pattern     => 'lab/' );
    ords.define_template(
        p_module_name => 'customers.rest',
        p_pattern     => 'lab/:cust_id' );
    ords.define_handler(
        p_module_name => 'customers.rest',
        p_pattern     => 'lab/',
        p_method      => 'GET',
        p_source_type => ords.source_type_collection_feed,
        p_source      => 'select * from customers' );
    ords.define_handler(
        p_module_name => 'customers.rest',
        p_pattern     => 'lab/:cust_id',
        p_method      => 'GET',
        p_source_type => ords.source_type_collection_item,
        p_source      => 'select * from customers where cust_id=:cust_id' );
    ords.define_handler(
        p_module_name => 'customers.rest',
        p_pattern     => 'lab/',
        p_method      => 'POST',
        p_source_type => ords.source_type_plsql,
        p_source      => 'begin insert into customers (cust_first_name,cust_last_name,cust_gender,cust_year_of_birth,cust_marital_status,cust_street_address,cust_postal_code,cust_city,cust_country,cust_main_phone_number,cust_income_level,cust_credit_limit,cust_email) values (:cust_first_name,:cust_last_name,:cust_gender,:cust_year_of_birth,:cust_marital_status,:cust_street_address,:cust_postal_code,:cust_city,:cust_country,:cust_main_phone_number,:cust_income_level,:cust_credit_limit,:cust_email);:forward_location:=:cust_id;:status_code:=201;end;' );
    ords.define_handler(
        p_module_name => 'customers.rest',
        p_pattern     => 'lab/:cust_id',
        p_method      => 'PUT',
        p_source_type => ords.source_type_plsql,
        p_source      => 'begin update customers set cust_first_name=:cust_first_name,cust_last_name=:cust_last_name,cust_gender=:cust_gender,cust_year_of_birth=:cust_year_of_birth,cust_marital_status=:cust_marital_status,cust_street_address=:cust_street_address,cust_postal_code=:cust_postal_code,cust_city=:cust_city,cust_country=:cust_country,cust_main_phone_number=:cust_main_phone_number,cust_income_level=:cust_income_level,cust_credit_limit=:cust_credit_limit,cust_email=:cust_email where cust_id=:cust_id; :forward_location:=:cust_id;:status_code:=200;end;' );
    ords.define_handler(
        p_module_name => 'customers.rest',
        p_pattern     => 'lab/:cust_id',
        p_method      => 'DELETE',
        p_source_type => ords.source_type_plsql,
        p_source      => 'begin delete customers where cust_id=:cust_id;:status_code:=200;end;' );
    COMMIT;
end;/
```
- You have just created the base path "CUSTOMERS", that will be used to access this RESTful service and the URI Template "LAB" that will be used to access the specific resource. The URI Template for the resource is appended to the server path and module base path.

![](./images/step6/1.sqldev-cont4.png)

- If you copy the full URL and paste in the browser, you will get JSON dataset. 

![](./images/step6/1.sqldev-cont5.PNG)
- Congratulations, you are now able utilize ATP using RESTful services.

## Create your second workspace RESTATP and create an empty application.

-  You will follow same steps as we did in [step 4](step4.md). Logout from your current APEX workspace, and login as **ADMIN** user. When you are logging as **ADMIN** user, name of the workspace is **INTERNAL** and password is your database password which you have provided in ATP instance provisioning.

  ![](./images/step6/2.websource.PNG)

- Click on **Create workspace** to configure your second APEX workspace. Let's name it **RESTATP** and remember *keep note of the password as you will need it later.*
  
  ![](./images/step6/2.websource-cont1.PNG)
  
- New workspace and database user is created. Now click on hyperlink "RESTATP".

  ![](./images/step6/2.websource-cont2.PNG)
  
- Provide your password when you created "RESTATP" user in previous step.

  ![](./images/step6/2.websource-cont2_1.PNG)

## You may continue to next step 
- [Utilize RESTful service from APEX](step7.md)

## Follow-up questions

![](./images/bilegt.jpg)

[bilegt.bat.ochir@oracle.com](mailto:bilegt.bat.ochir@oracle.com)
