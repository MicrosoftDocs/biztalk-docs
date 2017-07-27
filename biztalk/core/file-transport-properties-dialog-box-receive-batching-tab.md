---
title: "File Transport Properties Dialog Box, Receive, Batching Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.file.transport.receive.batching"
helpviewer_keywords: 
  - "batching, file transport"
  - "file transport, properties"
  - "file transport, configuring"
  - "configuring, file transport"
  - "file transport, batching"
ms.assetid: d510de47-ad5b-4499-8ec8-c99d372078a3
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Transport Properties Dialog Box, Receive, Batching Tab
Use the **Batching** tab to configure the receive location for the File adapter.  
  
 **Number of messages in a batch**  
 Specify the maximum number of messages to be submitted in a batch.  
  
 Default Value: 20  
  
 Type: Int  
  
 Minimum value: 1  
  
 Maximum value: 256  
  
 **Maximum batch size (in bytes)**  
 Specify the maximum total bytes for a batch.  
  
 Default Value: 102400  
  
 Type: Int  
  
 Minimum value: 1024  
  
 Maximum value: MAX_LONG  
  
## See Also  
 [How to Configure a File Receive Location](http://msdn.microsoft.com/library/09736a30-885b-4ecf-a2e0-0f9d064e4ee6)   
 [Restrictions on the File Mask and File Name Properties](http://msdn.microsoft.com/library/d8f5afd0-a61f-4c9b-8a57-4792e3054769)