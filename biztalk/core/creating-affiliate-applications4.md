---
title: "Creating Affiliate Applications4 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tickets, Single Sign-On"
  - "affiliate applications, setting credentials"
  - "affiliate applications"
  - "Single Sign-On, creating tickets"
  - "SSO tickets"
ms.assetid: 790fbe21-8081-4d57-803f-23014c8a3135
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Affiliate Applications
The following steps describe how to get started with affiliate applications using SSO.  
  
> [!NOTE]
>  If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service. SSO only functions under a domain account.  
  
### To create an affiliate application  
  
1. In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.  
  
2. In a command prompt, change directories to the Enterprise Single Sign On folder.  
  
    For example:  
  
    **C:\Program Files\Common Files\Enterprise Single Sign-On>**  
  
3. Use the Enterprise Single Sign-On commands. For a list of commands, use the **-help** switch.  
  
4. To create the affiliate application using *.XML as a beginning, type the following command:  
  
    `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
    where:  
  
   - C:\SSOtest is the folder that contains your application XML.  
  
   - AffiliateApplication.xml is the application XML you created that contains the Sign-On information.  
  
     For example:  
  
   ```  
   <?xml version="1.0"?>  
   <SSO>  
       <application name="JDEdwardsApp">  
           <description>JDEdwards SSO Application</description>  
           <contact>someone@microsoft.com</contact>  
           <userGroup>ibi\Domain Users</userGroup>  
           <!—an existing group on the domain controller - >   
           <appAdminGroup>ibi\YourID</appAdminGroup>  
           <!-- an existing account within the domain group - >   
  
           <field ordinal="0" label="User ID" masked="no" />  
           <field ordinal="1" label="Password" masked="yes" />  
           <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
  
       </application>  
   </SSO>  
   ```  
  
### To create Single Sign-On tickets  
  
1.  Type the following command to control SSO ticket behavior:  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Answer the following questions as shown:  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     On completion, you receive the following confirmation:  
  
     **Using SSO server on this computer. The operation completed successfully.**  
  
### To enable affiliate application XML  
  
1. Type the following command:  
  
    `ssomanage -enableapp JDEdwardsApp`  
  
2. Type the following command to list the applications and to verify that the application was created:  
  
    `ssoclient.exe –listapps`  
  
    The affiliate applications that are available for use display in a list:  
  
    **Applications available for IBI\YourID - JDEdwardsApp**  
  
3. Type the following command to set the affiliate application credentials:  
  
    `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4. Enter the user name and password at the prompts. Enter the logon credentials for the JDEdwardsApp affiliate application.  
  
    For example, enter the user identification and the password for that user to enter into the system through the SSO server.  
  
   - User ID: **user**  
  
   - Password: `******`  
  
   - Confirm? Password: `******`  
  
     The affiliate application appears in the BizTalk Adapter for JD Edwards EnterpriseOne **Transport Properties** dialog box.  
  
## See Also  
 [Security in BizTalk Adapter for JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)