---
description: "Learn more about: How to Configure SSO Using the Configuration Wizard"
title: "How to Configure SSO Using the Configuration Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 064cc764-e739-4261-bb05-6da0fa5889c1
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Configure SSO Using the Configuration Wizard
Use the **Enterprise Single Sign-On (SSO)** page to configure your SSO settings.  
  
> [!NOTE]
>  You will not be able to reconfigure SSO in the configuration manager after you have configured it.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable Enterprise Single Sign-On on this computer**|Select **Enable Enterprise Single Sign-On on this computer** to configure this server with SSO settings.|  
|**Create a new SSO system**|Select **Create a new SSO system** if this is the first SSO server you are configuring in your SSO system. This also creates and configures the SSO Credential database. You must also back up the secret on this secret server. **Caution:**  You should configure the master secret server as a stand-alone server. You must be an SSO administrator while performing this configuration task. **Note:**  Only one master secret server can be associated with one SSO group. Associating two master secret servers to the same SSO group is not supported.|  
|**Join an existing SSO system**|Select **Join an existing SSO system** to connect to an existing SSO system.|  
|**Data stores**|The **Data stores** list provides an editable view of the data stores used for the SSO database.|  
|**Windows service**|The **Windows service** list provides an editable view of the account used to run the Enterprise Single Sign-On service.|  
|**Windows accounts**|The **Windows accounts** list provides an editable view of the SSO Administrators and SSO Affiliate Administrators Windows groups.|  
  
 Use the **Enterprise Single Sign-On Secret Backup** page to save the master secret to an encrypted backup file in the event that disaster recovery is needed.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Secret backup password**|Type the password for the backup file.|  
|**Confirm password**|Confirm the password for the backup file.|  
|**Password reminder**|Type a reminder for the password you enter.|  
|**Backup file location**|Provide a file name and file path to the secret backup file. By default it is stored at \<drive>:\Program Files\Common Files\Enterprise Single Sign-On\\.|  
  
## Considerations for Configuring SSO  
 When you configure Enterprise SSO, consider the following:  
  
-   When configuring the SSO Windows accounts using local accounts, you must specify the account name without the computer name.  
  
-   When using a local SQL Server named instance as data store, you must use LocalMachineName\InstanceName instead of LocalMachineName\InstanceName, PortNumber.  
  
-   It is possible to configure the Enterprise SSO service account as the Network Service account. To do so, you must first add the Network Service account to the SSO Administrators group and reboot the computer for the change to take effect.  
  
> [!IMPORTANT]
>  While it is possible to do this, it is not a good security practice, as the Network Service account is a low privilege account.
