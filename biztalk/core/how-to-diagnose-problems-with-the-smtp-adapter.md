---
description: "Learn more about: How to Diagnose Problems with the SMTP Adapter"
title: "How to Diagnose Problems with the SMTP Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
