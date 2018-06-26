---
title: "How to Diagnose Problems with the FTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 499d23d3-b705-4527-9929-147be157e6b3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Diagnose Problems with the FTP Adapter
This section contains steps that can be followed to help diagnose problems with the FTP adapter.  
  
### Check the FTP log files on the FTP Server for errors  
  
- The source or target FTP server log files can contain information that is helpful for troubleshooting problems with the FTP adapter. By default the FTP log files on a Windows Server or Windows XP computer are located in the following directory:  
  
   <em>%WinDir%\\</em>system32\LogFiles\MSFTPSVC1\  
  
  > [!NOTE]
  >  *%WinDir%* is a placeholder for the location of the Windows directory on the FTP server.  
  
### Enable logging for the FTP Receive location or Send Port  
  
-   Configure the FTP receive location or send port with a **Log** folder. The FTP adapter will save detailed logging information to this folder. The **Log** folder option is available on the **FTP Transport Properties** dialog box when configuring a receive location or send port with the FTP transport type.  
  
## See Also  
 [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md)