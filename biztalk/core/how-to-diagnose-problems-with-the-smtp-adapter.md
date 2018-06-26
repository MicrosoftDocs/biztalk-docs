---
title: "How to Diagnose Problems with the SMTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eaf39fd8-b662-4b0c-b5e8-1af02cb4f79b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Diagnose Problems with the SMTP Adapter
This section contains steps that can be followed to help diagnose problems with the SMTP adapter.  
  
### Check the SMTP log files of the SMTP Server for errors  
  
- The target SMTP server log files can contain information that is helpful for troubleshooting problems with the SMTP adapter. By default the SMTP log files on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] are located in the following directory:  
  
   <em>%WinDir%\\</em>system32\LogFiles\SMTPSVC1\  
  
  > [!NOTE]
  >  *%WinDir%* is a placeholder for the location of the Windows directory on the SMTP server.  
  > 
  > [!NOTE]
  >  SMTP logging is disabled by default on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]. For information about enabling logging for SMTP, see the Windows Server documentation.  
  
## See Also  
 [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Troubleshooting the SMTP Adapter](../core/troubleshooting-the-smtp-adapter.md)