---
title: "Sending and Receiving Large Messages Using the MSMQ Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, large messages"
  - "configuring [MSMQ adapters], large messages"
  - "MSMQ adapters, large messages"
ms.assetid: 208efbed-7b58-4da5-ba27-65a315c2713b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending and Receiving Large Messages Using the MSMQ Adapter
The MSMQ adapter default message handling depends, in part, on the size of the message. When a message is less than four megabytes (4 MB), the MSMQ adapter uses the .NET Framework Class Library. Otherwise, it uses the large message extensions in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 If your application consistently receives or sends large messages, you may have to control the amount of memory that the adapter uses. For more information about conserving memory, see [Optimizing Performance of the MSMQ Adapter](../core/optimizing-performance-of-the-msmq-adapter.md).  
  
## See Also  
 [Optimizing Performance of the MSMQ Adapter](../core/optimizing-performance-of-the-msmq-adapter.md)   
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)