---
description: "Learn more about: Creating Affiliate Applications"
title: "Creating Affiliate Applications for TIBCO Rendezvous | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3603fcb-3594-460b-b74a-618e22d9c4e0
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Affiliate Applications
The following steps describe how to start working with affiliate applications and Single Sign-On (SSO). For complete information about how to use Enterprise Single Sign-On, see the Microsoft documentation.  
  
> [!NOTE]
>  If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service. SSO only functions under a domain account.  
  
## Create an affiliate application  
  
1.  In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.  
  
2.  In a command prompt, change directories to the Enterprise Single Sign-On folder. For example:  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-On>**  
  
3.  Use the Enterprise Single Sign-On commands. For a list of commands, use the **-help** switch.  
  
4.  To create the affiliate application by using *.XML as a start, type the following command:  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     Where:  
  
     C:\SSOtest is the folder that contains your application XML.  
  
     AffiliateApplication.xml is the application XML you created that contains the Sign-On information.  
  
     For example:  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO RendezvousApp">  
            <description> TIBCO Rendezvous SSO Application</description>  
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
  
## Create Single Sign-On tickets  
  
1.  Type the following command to control SSO ticket behavior:  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Answer the following questions as shown:  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
3.  On completion, you receive the following confirmation:  
  
     **Using SSO server on this computer. The operation completed successfully.**  
  
## Enable affiliate application XML  
  
1.  Type the following command:  
  
     `ssomanage -enableapp TIBCO RendezvousApp`  
  
2.  Type the following command to list the applications and to verify that the application was created:  
  
     `ssoclient.exe –listapps`  
  
     The affiliate applications that are available for use appear in a list.  
  
     **Applications available for IBI\YourID - TIBCO RendezvousApp**  
  
3.  Type the following command to set the affiliate application credentials:  
  
     `ssoclient.exe -setcredentials TIBCO RendezvousApp`  
  
4.  Enter the User name and password at the prompts.  
  
5.  Enter the logon credentials for the TIBCO RendezvousApp affiliate application.  
  
     For example, enter the user identification and the password for the user to enter into the system through the SSO server.  
  
    -   User ID: user  
  
    -   Password: ******  
  
    -   Confirm Password: ******  
  
6.  The affiliate application appears in the BizTalk Adapter for TIBCO Rendezvous **Transport Properties** dialog box.  
  
## See Also  
 [Security in BizTalk Adapter for TIBCO Rendezvous](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)   
