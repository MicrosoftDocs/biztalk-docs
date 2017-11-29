---
title: "Viewing and Interpreting Audited Events1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed0376bb-3336-4282-acae-d55e97160146
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Viewing and Interpreting Audited Events
Events audited by Host Integration Server are recorded on the server in which they occur. They are not stored centrally, in contrast with other records generated through Host Integration Server.  
  
 The records generated through auditing are stored in the security section of the event log. In contrast, other Host Integration Server events are recorded in the application section of the log.  
  
> [!NOTE]
>  When you view log entries for audited events related to Host Integration Server, you will see a record of actions carried out by Host Integration Server itself, as well as actions carried out by users. The source of the actions carried out by Host Integration Server is the account under which the service is running.  
  
 The event details for some events will list an item called **Accesses** in the **Description** box. Unusual information may be shown here for events related to Host Integration Server.  
  
 Use the following table for interpreting this information.  
  
|Information shown for Accesses (under Description)|Meaning|  
|----------------------------------------------------------|-------------|  
|Unknown specific access (bit 0)|Read Domain access. This access applies when someone starts or attempts to start the Host Integration Server SNA Manager. (Host Integration Server must read the configuration file in order to function.)|  
|Unknown specific access (bit 1)|Write Domain access. This access applies when someone starts the Host Integration Server SNA Manager in write mode — that is, when someone starts Host Integration Server and the primary Host Integration Server computer is available.|  
|Unknown specific access (bit 2)|Manage Domain access. This access applies when someone starts or attempts to start the Host Integration Server SNA Manager.|  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security.md)