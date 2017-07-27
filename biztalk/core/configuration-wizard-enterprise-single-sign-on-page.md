---
title: "Configuration Wizard, Enterprise Single Sign-On Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.config.wizard.sso"
ms.assetid: 15c013f1-a7ff-4c56-a6e6-babf3c3d38ae
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration Wizard, Enterprise Single Sign-On Page
Use the **Enterprise Single Sign-On (SSO)** page to configure SSO settings for your BizTalk Server environment.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable Enterprise Single Sign-On on this computer**|Select **Enable Enterprise Single Sign-On on this computer** to configure this server with SSO settings.|  
|**Create a new SSO system**|Select **Create a new SSO system** if this is the first SSO server you configure in your SSO system. This will also create and configure the SSO database. You must also back up the secret on this secret server. **Important:**  You should configure the master secret server as a stand-alone server. You must be an SSO administrator while performing this configuration task.|  
|**Join an existing SSO system**|Select **Join an existing SSO system** to connect to an existing SSO system in the BizTalk Server environment.|  
|**Data stores**|The Data stores list provides an editable view of the data stores used for the SSO database.|  
|**Windows service**|The Windows service list provides an editable view of the account used to run the Enterprise Single Sign-On service.|  
|**Windows accounts**|The Windows accounts list provides an editable view of the SSO Administrators and SSO Affiliate Administrators Windows groups.|  
  
 Use the **Enterprise Single Sign-On Secret Backup** page to save the master secret to an encrypted backup file in case of system recovery.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Secret backup password**|Type the password for the backup file.|  
|**Confirm secret backup password**|Confirm the password for the backup file.|  
|**Secret backup reminder**|Type a reminder for the password you enter.|  
|**Secret backup file**|Provide a file name and file path to the secret backup file. By default it is stored at \Program Files\Common Files\Enterprise Single Sign-On\\.|  
  
## See Also  
 [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [Getting Started](../core/getting-started-with-biztalk-server.md)