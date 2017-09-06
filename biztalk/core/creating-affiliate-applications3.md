---
title: "Creating Affiliate Applications3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affiliate applications"
  - "Single Sign-On, creating tickets"
  - "tickets, creating Single Sign-On"
  - "affiliate applications, creating"
  - "SSO tickets"
ms.assetid: 800644fd-2286-4e59-894b-260f584dd29f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Affiliate Applications
The following steps describe how to get started with affiliate applications using Single Sign-On (SSO).  
  
> [!NOTE]
>  If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, because this affects the function of the ESSO service. SSO only functions under a domain account.  
  
## Creating an Affiliate Application  
  
#### To create an affiliate application  
  
1.  In **Control Panel**, open **Services**, and verify that the Enterprise Single Sign-On service is running.  
  
2.  In a command prompt, change directories to the Enterprise Single Sign-On folder.  
  
     For example:  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-On>**  
  
3.  Use the Enterprise Single Sign-On commands. For a list of commands, use the -help switch.  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  To create the affiliate application using the *.XML as a beginning, type in the following command:  
  
     **ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml**  
  
     where:  
  
     C:\SSOtest is the folder containing your application XML.  
  
     AffiliateApplication.xml is the application XML you created containing the Sign On information.  
  
     For example:  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="JDEdwardsApp">  
              <description>JDEdwards SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
              <userGroup>ibi\Domain Users</userGroup>  
              <!—-an existing group on the domain controller - >   
              <appAdminGroup>ibi\YourID</appAdminGroup>  
              <!-- an existing account within the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## Creating Single Sign-On Tickets  
  
#### To create SSO tickets  
  
1.  Type in the following command to control SSO ticket behavior:  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Answer the questions:  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     On completion you receive a confirmation:  
  
     **Using SSO server on this computer. The operation completed successfully.**  
  
## Enabling the Affiliate Application XML  
  
#### To enable affiliate application XML  
  
1.  Type in the following command:  
  
     `ssomanage -enableapp JDEdwardsApp`  
  
2.  Type in the following command to list the applications and to verify that the application was created:  
  
     `ssoclient.exe –listapps`  
  
     The Affiliate Applications available for use appear in a list.  
  
     **Applications available for IBI\YourID - JDEdwardsApp**  
  
3.  Type in the following command to set the affiliate application credentials:  
  
     `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4.  Enter the user name and password at the prompts. Enter the logon credentials for the JDEdwardsApp affiliate application. For example, enter the user identification and the password for that user to enter into the system through the SSO server.  
  
    -   **User ID:** user  
  
    -   **Password:** ******  
  
    -   **Confirm? Password:** ******  
  
5.  The affiliate application appears in the drop-down list of the BizTalk Adapter for JD Edwards OneWorld Transport Properties dialog box.  
  
## See Also  
 [Using Single Sign-On](../core/using-single-sign-on3.md)