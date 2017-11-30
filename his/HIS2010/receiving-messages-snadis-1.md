---
title: "Receiving Messages (SNADIS)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ade6aa6a-a44d-4316-8410-343f17078e77
caps.latest.revision: 3
---
# Receiving Messages (SNADIS)
The Base calls the SNALink dispatcher function [SNALinkDispatchProc](../HIS2010/snalinkdispatchproc1.md) when a message is available for it.  
  
 Note that after the application receives a message, it is responsible for the buffer in which the message was received. It must either reuse the buffer to send a message (using [SNASendMessage](../HIS2010/snasendmessage2.md)) or release it (using [SNAReleaseBuffer](../HIS2010/snareleasebuffer2.md)). If the buffer to be reused does not contain the correct number of elements for the message to be sent, the application can obtain additional elements (using [SNAGetElement](../HIS2010/snagetelement2.md)) or release existing ones (using [SNAReleaseElement](../HIS2010/snareleaseelement2.md)).