---
title: "Create affiliate applications for TIBCO EMS | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 191e5b56-dab9-4bf3-9f89-a900907d64e0
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create Affiliate Applications
The following steps describe how to start using affiliate applications and Single Sign-On (SSO).  
  
> [!NOTE]
>  If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server; this affects the function of the Enterprise SSO service. SSO only functions under a domain account  
  
## Create an affiliate application  
  
1. In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.  
  
2. In a command prompt, change directories to the Enterprise Single Sign-On folder.  
  
    For example:  
  
    **C:\Program Files\Common Files\Enterprise Single Sign-On>**  
  
3. Use the Enterprise Single Sign-On commands. For a list of commands, use the **-help** switch.  
  
4. To create the affiliate application by using *.XML as a start, type the following command:  
  
    `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
    where:  
  
   - C:\SSOtest is the folder that contains your application XML.  
  
   - AffiliateApplication.xml is the application XML you created that contains the Sign-On information.  
  
     For example:  
  
   ```  
   <?xml version="1.0"?>  
   <SSO>  
       <application name="TIBCO EMS App">  
           <description>TIBCO EMS SSO Application</description>  
           <contact>someone@example.com</contact>  
           <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
           <!—an existing group on the domain controller - >   
           <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
           <!-- an existing account in the domain group - >   
           <field ordinal="0" label="User ID" masked="no" />  
           <field ordinal="1" label="Password" masked="yes" />  
           <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
       </application>  
   </SSO>  
   ```  
  
   By using the example XML, the affiliate application, TIBCO EMS App, contains the values as shown in the command prompt.  
  
## Create Single Sign-On tickets  
  
1.  Type the following command to control SSO ticket behavior:  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Answer the questions:  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     On completion, you receive a confirmation:  
  
     **Using SSO server on this computer. The operation completed successfully.**  
  
## Enable affiliate application XML  
  
1. Type the following command:  
  
    `ssomanage -enableapp TIBCO EMSApp`  
  
2. Type the following command to list the applications and to verify that the application was created:  
  
    `ssoclient.exe –listapps`  
  
    The affiliate applications that are available for use appear in a list:  
  
    **Applications available for IBI\YourID - TIBCO EMSApp**  
  
3. Type the following command to set the affiliate application credentials:  
  
    `soclient.exe -setcredentials TIBCO EMSApp`  
  
4. Enter the user name and password at the prompts. Enter the logon credentials for the TIBCO EMS App affiliate application.  
  
    For example, enter the user identification and the password for that user to enter into the system through the SSO server.  
  
   - User ID: **user**  
  
   - Password: `******`  
  
   - Confirm? Password: `******`  
  
     The affiliate application appears in the BizTalk Adapter for TIBCO EMS **Transport Properties** dialog box.  
  
## See Also  
[Secure the adapter](../core/security-in-biztalk-adapter-for-tibco-ems.md)