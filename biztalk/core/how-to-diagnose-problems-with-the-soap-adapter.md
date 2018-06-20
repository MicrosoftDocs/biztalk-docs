---
title: "How to Diagnose Problems with the SOAP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16c93333-cb32-49bc-a1c4-9d726ab41850
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Diagnose Problems with the SOAP Adapter
This section contains steps that can be followed to help diagnose problems with the SOAP adapter.  
  
### Check the IIS log and HTTPERR log of the IIS Server for errors  
  
- The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the SOAP adapter. By default the IIS log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] computer are located in the following directory:  
  
   <em>%WinDir%\\</em>system32\LogFiles\W3SVC1\  
  
  > [!NOTE]
  >  *%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.  
  
   By default the HTTPERR log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] based computer are located in the following directory:  
  
   <em>%WinDir%\\</em>system32\LogFiles\HTTPERR\  
  
  > [!NOTE]
  >  The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.  
  
## See Also  
 [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Troubleshooting the SOAP Adapter](../core/troubleshooting-the-soap-adapter.md)