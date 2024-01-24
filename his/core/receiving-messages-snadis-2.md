---
description: "Learn more about: Receiving Messages (SNADIS)"
title: "Receiving Messages (SNADIS)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Receiving Messages (SNADIS)
The Base calls the SNALink dispatcher function [SNALinkDispatchProc](./snalinkdispatchproc2.md) when a message is available for it.  
  
 Note that after the application receives a message, it is responsible for the buffer in which the message was received. It must either reuse the buffer to send a message (using [SNASendMessage](./snasendmessage1.md)) or release it (using [SNAReleaseBuffer](./snareleasebuffer1.md)). If the buffer to be reused does not contain the correct number of elements for the message to be sent, the application can obtain additional elements (using [SNAGetElement](./snagetelement1.md)) or release existing ones (using [SNAReleaseElement](./snareleaseelement1.md)).
