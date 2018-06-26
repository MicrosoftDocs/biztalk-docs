---
title: "Troubleshooting Enterprise Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb54af9f-a6ef-46c1-b987-2019cff3f837
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Enterprise Single Sign-On
This topic describes information about common problems you may encounter while using Enterprise Single Sign-On (SSO).  

 As you begin to troubleshoot your SSO environment, it may be useful to walk through the items in the following table to ensure all components are working as expected:  


|                                                                      Question                                                                      |                                                                                                                                                                                                                      Comments                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                        Is there anything in the Application event log from the SSO system?                                         | The SSO messages in the event log can help you narrow down the problem in the SSO system. The source of the messages from the SSO system is ENTSSO. **Important:**  Many of the SSO errors and events appear as Warnings in the event log, not as Errors. The SSO system generates a Warning when the problem affects a single client of the SSO service, whereas it generates Errors when the problem affects the entire SSO system (all clients). |
| Is the SSO service installed correctly?<br /><br /> Does it start as expected?<br /><br /> Under which service account is the SSO service running? |                                                                                                                                                               Ensure the SSO service is correctly installed, and that the service account is member of the SSO administrators group.                                                                                                                                                                |
|                                                             Where is the SSO database?                                                             |                                                                                                                           Use the command line **ssoconfig -showdb**. For more information about this command, see [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md).                                                                                                                           |
|                                                          Which SSO server is being used?                                                           |                                                                                                                                           Use the command line **ssomanage -showserver**. For more information about this command, see [How to Set the SSO Server](../core/how-to-set-the-sso-server.md).                                                                                                                                           |
|                                                       What is the SSO Administrator account?                                                       |                                                                                                                         Use the command line **ssomanage –displaydb**. For more information about this command, see [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md).                                                                                                                          |
|                                                          Is everything correctly enabled?                                                          |                                                                                                                         Use the command line **ssomanage –displaydb**. For more information about this command, see [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md).                                                                                                                          |
|                                                        Do the affiliate applications exist?                                                        |                                                                                                                                 Use the command line **ssomanage –listapps all**. For more information about this command, see [How to List Affiliate Applications](../core/how-to-list-affiliate-applications.md).                                                                                                                                 |
|               Does the specific affiliate application look correct?<br /><br /> What accounts are using this affiliate application?                |                                                                                               Use the command line **ssomanage –displayapp**<em>\<application name\></em>. For more information about this command, see [How to List the Properties of an Affiliate Application](../core/how-to-list-the-properties-of-an-affiliate-application.md).                                                                                                |
|                                               Are there any mappings for this affiliate application?                                               |                                                                                                                           Use the command line **ssomanage –listmappings**<em>\<application name\></em>. For more information about this command, see [How to List User Mappings](../core/how-to-list-user-mappings.md).                                                                                                                            |
|                                                    What accounts are members of the SSO groups?                                                    |                                                                                                                                                                                            Verify the group membership for all SSO groups and accounts.                                                                                                                                                                                             |
|                                          Is the COM+ application for the SSO server running as expected?                                           |                                                                                                                                                  Verify the COM+ application SSO server. **Note:**  You can also check the event log for detailed information, such as event and warning messages.                                                                                                                                                  |

## Known Issues  

#### ENTSSO Service Fails to Start  

##### Problem  
 The ENTSSO service fails to start.  

##### Cause  
 If the ENTSSO service is not running under a valid SSO Administrator account, it will fail to start.  

##### Resolution  
 Specify a valid SSO administrator account for the ENTSSO Service and restart the service from Services Control Manager (SCM) snap-in.  

#### BizTalk Services Dependent on the Enterprise Single Sign-On Service (ENTSSO) fail to start after a reboot  

##### Problem  
 BTSSvc$BizTalkServerApplication has a dependency on the Enterprise Single Sign-On Service (ENTSSO) and may timeout during start up after a reboot.  

##### Cause  
 The Enterprise Single Sign-On Service may take around 3 minutes to start.  

##### Resolution  
 Configure the “BizTalk Service BizTalk Group: BizTalkServerApplication” service with the Automatic (Delayed Start) startup type option. This will initiate the start of the service after all Automatic services have completed their startup routines.  

#### Cannot Access an Affiliate Application  

##### Problem  
 The Enterprise Single Sign-On service disables an affiliate application if the application administrator account associated with it is not valid.  

##### Cause  
 The SSO application administrator account is not valid.  

##### Resolution  
 Ensure that the SSO application administrator account is valid before you create an affiliate application. You must then enable the affiliate application to use the application.  

#### RPC Error Occurs When Connecting to a Client Computer  

##### Problem  
 When a user runs a command such as **ssomanage -displayapp**<em>\<applicationname\></em>, where the computer attempt to connect to a remote SSO Server to retrieve the information, they receive the following error: ERROR: 0x800706BA: The RPC server is unavailable.  

##### Cause  
 This error occurs when the user specifies the wrong server information, or when the SSO Service is not available on the remote server.  

##### Resolution  

-   Follow the steps in [How to Set the SSO Server](../core/how-to-set-the-sso-server.md) to make sure you are connected to the correct SSO Server.  

-   Make sure the SSO Service is enabled and running in the SSO Server to which you are connecting.  

#### Master Secret Is Missing or Corrupt  

##### Problem  
 The master secret is missing or corrupt. It normally generates during configuration. If the secret is missing, one of the following messages will display in the event log as the Enterprise Single Sign-On service starts.  

 MessageId=10520  

 Severity=Warning  

 SSO_WARN_NO_SECRETS  

 MessageId=10565  

 Severity=Error  

 SSO_ERROR_SECRET_VALIDATE_FAILED  

 MessageId=10521  

 Severity=Error  

 SSO_ERROR_SECRETS_NOT_LOADED  

##### Cause  
 This problem can occur if a secret is generated while the Enterprise Single Sign-On service (SSO) was running under one service account, and then the service account was changed. The secret is stored in the registry in encrypted form, and is encrypted using a key based on the identity of the service account (which ENTSSO runs under).  

##### Resolution  
 Change the service account ENTSSO is running under to the original service account when the master secret was created.  

 To change the ENTSSO service account:  

1.  Back up the master secret. For more information, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).  

2.  Stop Enterprise Single Sign-On Services.  

3.  Change the service account.  

4.  Restart SSO and ignore any event log errors about a corrupted secret.  

5.  Restore the master secret. For more information, see [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md).  

## See Also  
 [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)