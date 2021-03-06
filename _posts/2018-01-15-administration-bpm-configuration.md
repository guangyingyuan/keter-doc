---
layout: page
title: "BPM configuration"
category: administration
date: 2018-01-05 15:17:55
order: 2
---

### Add bpm server
  1. Click **Administrator** tab, then switch to  **BPM configurtaion** tab to manage BPM server.  
  
  2. Click **add new row** icon to add new BPM server.  
  
     ![][administrator_bpmserver]  

      |   Field                | Description                                                             |
      | ---------------------- |-------------------------------------------------------------------------|                                          
      | Server Name            | BPM server name                                                                        |  
      | Type                   | DEV, QA, STG, PRO                                                          |
      | BPM Version            | BPM version                                                                        |
      | Server Url             | BPM server URL, eg: https://bpmserver:9443                     |                                                                        
      | SOAP port              | soap port defined in Was console                                |
      | SSH User Name          | used for snapshot deployment from PC to PS                            | 
      | SSH key                | used for snapshot deployment from PC to PS                           |
      | WAS admin Command      | the path of wsadmin.sh  in linux server                                 |      
      | Rest User Name         | bpm server rest api username                                            |
      | Rest Password          | bpm server rest api password                                            |   
      | WAS Admin username     | was admin name                                                                        |
      | WAS Admin password     | was admin password                                                                        |  
      | Connected Server Name  | online PS server name               |
      | Rest Uri               | bpm rest uri, eg: /rest/bpm/wle/v1                                                           |   


### Edit BPM server
  Select the server in the **BPM Configuration** table, then click the	**edit** icon to edit BPM server. 


### Delete bpm server
  Select the server in the **BPM Configuration** table, then click the **delete** icon to delete bpm server. 

### Add user to bpm server
  1. Select the server in the **BPM Configuration** table, then click the **Bpm User** icon to add user. Then you can see the bpm user list table. 
  
  2. Click **add new row** icon from bpm user table to add a new bpm user.  
	
     ![][administrator_bpmuser]           
	  
	 |   Field                | Description                                                             |
     | ---------------------- |-------------------------------------------------------------------------|                                          
     | User    Name           | the user name of BPM server                                              |  
     | Display Name           | the display name of BPM user                                          |
     | User Password          | the password of BPM user                                                |
     | Role                   | the logical role name of BPM user                                                    |  
 

  After adding user, you can see the user list for this BPM server.
  
  ![][administrator_bpmuserlist]    
	
**Notes:**   
You need to well define the **Display name** of the BPM user, as it will be the **assignee** display name for the test steps in the test case.
  
[administrator_bpmserver]: ../images/administrator/administrator_bpmserver.png
[administrator_bpmuser]: ../images/administrator/administrator_bpmuser.png
[administrator_bpmuserlist]: ../images/administrator/administrator_userlist.png
