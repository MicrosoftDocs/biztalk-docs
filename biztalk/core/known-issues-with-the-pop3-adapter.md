---
title: "Known Issues with the POP3 Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6d621a2-4801-44fe-a266-d4c05ac82633
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with the POP3 Adapter
This section contains information that may help you avoid errors.  
  
## Known Issues  
  
#### The POP3 Adapter fails to process documents when running on a 64 bit operating system  
  
##### Problem  
 The POP3 Adapter will not process documents when running on a 64 bit operating system.  
  
##### Cause  
 The POP3 Adapter adapter handler is unable to run in a 64 bit host instance.  
  
##### Resolution  
 If you are running the POP3 Adapter on a 64 bit machine, configure the POP3 Adapter handlers to run in a 32 bit host. This option is available on the Host Properties page accessible from the BizTalk Administration console.  
  
## See Also  
 [Troubleshooting the POP3 Adapter](../core/troubleshooting-the-pop3-adapter.md)