---
layout: page
title: "Installing on WebSphere Liberty"
category: installation
date: 2018-01-05 15:17:55
order: 3
---

   
### Deployment


**Configure Keter parameters** 
 
Edit **keter.properties** under **conf** folder. This properties file contains three sections.

**#application-prod.yml**   
*  **spring.datasource.username** : MySQL username  
*  **spring.datasource.password** : MySQL password  
*  **spring.datasource.url** : MySQL database connection URL
*  **server.context-path** : default as  "/keter"  
*  **server.full-context-path** :
    "http://keterServerip:port/keter", this url should be same with the your keter application url
*  **checkstyle.dir**: your checkstyle report folder  
*  **engineConfig.screenshotDir** :  screenshot folder  
*  **smtp.host** ：your SMTP host    
*  **smtp.port** ：your SMTP port    
*  **email.from** ：sender Email address 
*  **spring.activemq.broker-url** ：the IP and Port of embedded ActiveMQ. It is only needed when you integrate Keter with BPM DEF[1] to have the monitoring feature.

 For the other properties, you can leave them as default values.
 
**#checkstyle.properties (Only for ODM installed)**
	
*  **resUser** : rule execution server username  
*  **resPassword** : rule execution server password  
*  **resUrl** : rule execution server url  
*  **resPort** : rule execution server port  

**#monitoring.properties (Only for BPM DEF Integration)**
	
*  **event_type** : event types to be stored in Keter database  
*  **track_serviceflow** : default as true  

It is only needed when you integrate Keter with BPM DEF[1] to have the monitoring feature. You can leave them as default values.

When you finish updating the properties, run **package.bat** to update the Keter war (e,g, *bpm-keter-web.war*) file under **build** folder. You need to define the **JAVA_HOME** variable and add the **$JAVA_HOME/bin** directory to your path before executing **package.bat**.
	
**Configure WAS Liberty**  

* Edit **server.xml** from *wlp/usr/servers/servername* folder.  Please ensure both httpPort and httpsPort are unique.

```    
 <!-- Enable features -->
    <featureManager>
        <feature>servlet-3.1</feature>
		<feature>ssl-1.0</feature>
        <feature>websocket-1.1</feature>
    </featureManager>

    <!-- This template enables security. To get the full use of all the capabilities, a keystore and user registry are required. -->
    
    <!-- For the keystore, default keys are generated and stored in a keystore. To provide the keystore password, generate an 
         encoded password using bin/securityUtility encode and add it below in the password attribute of the keyStore element. 
         Then uncomment the keyStore element. -->
    <!--
    <keyStore password=""/> 
    -->
    <webContainer invokeFlushAfterService="false"/>
    
    <!--For a user registry configuration, configure your user registry. For example, configure a basic user registry using the
        basicRegistry element. Specify your own user name below in the name attribute of the user element. For the password, 
        generate an encoded password using bin/securityUtility encode and add it in the password attribute of the user element. 
        Then uncomment the user element. -->
    <basicRegistry id="basic" realm="BasicRealm"> 
        <!-- <user name="yourUserName" password="" />  --> 
    </basicRegistry>
    
    <!-- To access this server from a remote client add a host attribute to the following element, e.g. host="*" -->
    <httpEndpoint id="defaultHttpEndpoint"
				  host="*"
                  httpPort="9081"
                  httpsPort="9443" />
				  

                  
    <!-- Automatically expand WAR files and EAR files -->
    <applicationManager autoExpand="true" startTimeout="360s" stopTimeout="120s"/> 
	<application type="war" id="keter" name="keter" location="${server.config.dir}/apps/bpm-keter-web.war">
		<classloader delegation="parentLast" />
    </application>
	
	<keyStore id="defaultKeyStore" password="keterAdmin" />

```  
    

* Copy **bpm-keter-web.war** application into the /usr/servers/<yourservername>/apps directory.

* Start Liberty server and visit the url like http://serverip:port/keter (port is defined in the server.xml).

For example:  
In Liberty installation bin folder you can use below command to start the server
**server start default** (default is your server name).

[1]: ../installation/installation-integrate-def.html






