---
title: "Sending Messages1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1818402-bf14-4705-b1f9-79fe9a6cde11
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Sending Messages
The 3270 emulator inserts a message in a buffer and then calls the DL-BASE to send it. The message contains source and destination locality partner indexes (LPIs), which are set up when the connection is opened. For more information, see [LPI Connections](../core/lpi-connections.md).  
  
 The application can either obtain a new buffer to contain the message to be sent (using [sepdbubl](../Topic/sepdbubl2.md)), or reuse a buffer in which it previously received a message. The application is responsible for any buffer it has obtained or in which it has received a message. The application must either use (or reuse) the buffer to send a message or release it (using [sepdburl](../Topic/sepdburl1.md)). If the buffer to be reused does not contain the correct number of elements for the message to be sent, the application can obtain additional elements (using [sbpibegt](../Topic/sbpibegt1.md)) or release existing ones (using [sbpiberl](../Topic/sbpiberl1.md)). In this case, it must also ensure that the **numelts** field in the buffer header indicates the correct number of elements.  
  
 The function used to send the message is [sbpusend](../Topic/sbpusend2.md).