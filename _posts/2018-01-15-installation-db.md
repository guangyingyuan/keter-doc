---
layout: page
title: "DB Configuration"
category: installation
date: 2018-01-05 15:17:55
order: 2
---

   
### DB Deployment

We use MySQL as the default database. You can get these sql scripts from **sql** folder from installation package.

**Create DB**   

Connect to the MySQL server and use MySQL command to create database. 
``` 
mysql> create database keter ;
```  

**Execute DB scripts**  

Connect to the mysql server and switch to the **keter** DB and execute DB scripts **schema-mysql.sql**, **data-mysql.sql** to create the database tables and populate data.

You can execute the script with the mysql source command to execute script.Pls replace **yoursqlpath** to path of the sql folder location.

``` 
mysql> use keter ;
mysql> source yoursqlpath\schema-mysql.sql ;
mysql> source  yoursqlpath\data-mysql.sql ;
```  

**Notes:**     
You might need to change **data-mysql.sql** script for the your organization name. Please  replace 'keter' to your company name occur in the below script.

``` 
INSERT INTO organization (company_name, active) VALUES ('keter', true);
INSERT INTO user (user_name, password, role, active, organization_id) 
VALUES ('keterAdmin', '12d9f16eff974ae7730525b0dda228e2', 'ADMIN', true, (SELECT id FROM organization where company_name = 'keter'));

```  
