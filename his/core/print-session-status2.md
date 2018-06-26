---
title: "Print Session Status2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7633fbdc-9a70-4d7b-86da-4c6fd08982e5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Print Session Status
There are several different messages that show the status of a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] print session:  
  
- Active  
  
- Inactive  
  
- Pending  
  
- In Session: Indicates the print server session is active, and the logical unit (LU) is bound. For Advanced Program-to-Program Communications (APPC), a conversation is allocated.  
  
- Offline: Indicates the print session has been created, but the print server is not aware of it.  
  
- Paused: Indicates the print server session is active, but the printing has been paused.  
  
  To view the status of a print session, simply select the print session in SNA Manager.  
  
> [!NOTE]
>  The status shown by the SNA Manager and the Diagnostic tool (DISPLAY.EXE) may appear to be different for a given item (for example, LU status). This is because the SNA Manager shows the currently active sessions. The Display tool shows what was negotiated during CNOS setup.  
  
## See Also  
 [Host Integration Server Status](../core/host-integration-server-status1.md)