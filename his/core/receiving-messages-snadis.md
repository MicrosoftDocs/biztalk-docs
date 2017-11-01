---
title: "Receiving Messages (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e68a82d-bafa-4c8a-ba3a-8c0bd7aa4a1d
caps.latest.revision: 3
---
# Receiving Messages (SNADIS)
The Base calls the SNALink dispatcher function [SNALinkDispatchProc](../Topic/SNALinkDispatchProc1.md) when a message is available for it.  
  
 Note that after the application receives a message, it is responsible for the buffer in which the message was received. It must either reuse the buffer to send a message (using [SNASendMessage](../Topic/SNASendMessage2.md)) or release it (using [SNAReleaseBuffer](../Topic/SNAReleaseBuffer2.md)). If the buffer to be reused does not contain the correct number of elements for the message to be sent, the application can obtain additional elements (using [SNAGetElement](../Topic/SNAGetElement2.md)) or release existing ones (using [SNAReleaseElement](../Topic/SNAReleaseElement2.md)).