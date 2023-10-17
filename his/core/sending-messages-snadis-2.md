---
description: "Learn more about: Sending Messages (SNADIS)"
title: "Sending Messages (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ab209f1-fc02-49c7-a0b6-ecd0647d9c88
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Sending Messages (SNADIS)
The SNALink should build a message in a buffer, and then call the Base to send it. The message contains source and destination LPIs, which are set up when the connection is opened. For more information, see [LPI Connections](../core/lpi-connections-snadis-2.md).  
  
 The SNALink can either obtain a new buffer to contain the message to be sent (using [SNAGetBuffer](./snagetbuffer1.md)) or reuse one in which it has previously received a message. The application is responsible for any buffer that it has obtained or in which it has received a message. It must either use (or reuse) the buffer to send a message or release it (using [SNAReleaseBuffer](./snareleasebuffer1.md)). If a buffer to be reused does not contain the correct number of elements for the message to be sent, the application can obtain additional elements (using [SNAGetElement](./snagetelement1.md)) or release existing ones (using [SNAReleaseElement](./snareleaseelement1.md)). It is the applications responsibility to maintain the **numelts** field in the message header.  
  
 The function used to send a message to the node is [SNASendMessage](./snasendmessage1.md).
