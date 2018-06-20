---
title: "Selecting the Logging Store | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, auditing"
  - "configuring, logging"
  - "logging, configuring"
  - "auditing, configuring"
ms.assetid: 6ba64c59-3a15-4c10-b44f-18e0e432c6d3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Selecting the Logging Store
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] provides you with the option to select a combination of different logging stores, such as [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI), [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log.  

 You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer to configure the logging store.  

 Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and select the logging store.  

### To open BTAHL7 Configuration Explorer  

-   Click **Start**, click **Programs**, click **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  

### To select the  logging store  

1. In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, on the **Global Settings** tab, do the following:  


   |     Use this      |                                                                                                                                     To do this                                                                                                                                     |
   |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      **WMI**      |                                                                                                      Select this option if you want to generate WMI notifications for BTAHL7.                                                                                                      |
   |      **SQL**      |                     Select this option if you want to use [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your  logging store. **Note:**  BTAHL7 automatically creates the tables required for  logging if they do not exist.                     |
   |  **SQL Server**   | Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name. This is required when you select the **SQL** option. The maximum allowed length is 64 characters.<br /><br /> The default server and database name is the configured BTAHL7 database. |
   | **Database name** |                                      Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name. This is required when you select the **SQL** option. The maximum allowed length is 128 characters.                                      |
   |  **Event  Log**   |          Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as your  logging store. You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.          |


2. Click **Save**.  

   > [!NOTE]
   >  The locale of the events logged by the  Logging event broker depend on the locale of the  Logging Service account.  
   > 
   > [!NOTE]
   >  When changing the  Logging Service account password, you should first change the password in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsAD](../../includes/btsad-md.md)] directory service, and then restart the  Logging Service after changing the  Logging Service password on every server running it.  

## See Also  
 [Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
 [Logging Configuration](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)