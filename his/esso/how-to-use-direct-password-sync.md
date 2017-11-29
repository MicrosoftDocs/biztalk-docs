---
title: "How to Use Direct Password Sync | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 100acde9-f482-4812-8fd2-c0c477317d81
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Use Direct Password Sync
This version of Enterprise Single Sign-On includes the Direct Password Sync from Windows feature. This enables you to bypass a Password Sync Adapter and update the password in the ENTSSO Credential Database directly from Windows.  
  
 Direct Password Sync from Windows is useful in the following situations:  
  
-   Your enterprise system requires Windows to Windows mapping.  
  
-   You need to update the External User’s password in the Credential Database directly when a password change occurs for the Windows user. You can change the password on the back-end system (that corresponds to the external user) by using other mechanisms. For example, you can use Microsoft Identity Integration Server to update passwords in Resource Access Control Facility (RACF) on an IBM Mainframe using the RACF Management Agent.  
  
### To enable Direct Password Sync  
  
1.  Open Enterprise Single Sign-On.  
  
2.  In the scope pane, click **Affiliate Applications**.  
  
3.  Right-click the appropriate **Affiliate Application**.  
  
4.  Click **Properties**.  
  
     The **Affiliate Applications Properties** dialog box appears.  
  
5.  Click the **Options** tab.  
  
6.  Select the **Direct Password Sync from Windows** check box.  
  
7.  Click **OK**.