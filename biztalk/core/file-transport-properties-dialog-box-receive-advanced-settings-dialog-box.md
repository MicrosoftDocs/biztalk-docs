---
title: "File Transport Properties Dialog Box, Receive, Advanced Settings Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.file.transport.receive.advanced"
helpviewer_keywords: 
  - "file transport, properties"
  - "file transport, configuring"
  - "file transport, advanced settings"
  - "configuring, file transport"
ms.assetid: 2f67a63c-57f2-4ba9-af7c-151817c32c97
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Transport Properties Dialog Box, Receive, Advanced Settings Dialog Box
Use the **File Transport Properties** dialog box to configure the receive location for the File adapter.  
  
 **Rename files while reading**  
 Specify whether to rename files before picking them up for processing. For more information about using this option, see the appropriate topics in See Also.  
  
 Default Value: False  
  
 Type: Boolean  
  
 **Polling interval (ms)**  
 Specify the interval in milliseconds that the File adapter will poll the specified location for new files.  
  
 Default Value: 60,000  
  
 Type: Int  
  
 Minimum value: 1,000 (set to 1 to disable polling)  
  
 Maximum value: 3,600,000  
  
 **Retry count**  
 Specify the number of times that the File adapter will attempt to delete a file that it has read and submitted to BizTalk Server.  
  
 Default Value: 5  
  
 Type: Int  
  
 Minimum value: 0  
  
 Maximum value: 100  
  
 **Retry interval (ms)**  
 Specify the initial interval in milliseconds that the File adapter waits before attempting to delete a file that it has read and submitted to BizTalk Server. This interval will double after each retry interval up to the specified maximum retry interval value.  
  
 Default Value: 10  
  
 Type: Int  
  
 Minimum value: 1  
  
 Maximum value: 1,000  
  
 **Maximum retry interval (ms)**  
 Specify the maximum retry interval time in milliseconds that the File adapter waits before attempting to delete a file that it has read and submitted to BizTalk Server.  
  
 Default Value: 300,000  
  
 Type: Int  
  
 Minimum value: 1,000  
  
 Maximum value: 900,000  
  
## See Also  
 [How to Configure a File Receive Location](http://msdn.microsoft.com/library/09736a30-885b-4ecf-a2e0-0f9d064e4ee6)   
 [Restrictions on the File Mask and File Name Properties](http://msdn.microsoft.com/library/d8f5afd0-a61f-4c9b-8a57-4792e3054769)   
 [File Adapter](../core/file-adapter.md)