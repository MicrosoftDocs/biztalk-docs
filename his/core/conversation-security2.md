---
description: "Learn more about: Conversation Security"
title: "Conversation Security2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1735d9d4-3300-4fca-a737-a7e090bcfc2a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Conversation Security
You can use conversation security to require that the invoking TP provide a user identifier and password before APPC will allocate a conversation with the invokable TP. If security is activated, the invoking TP must supply a combination of the user identifier and password as parameters of [ALLOCATE](./allocate2.md) or [MC_ALLOCATE](./mc-allocate2.md). Conversation security is activated and configured through registry or environment variables on the computer where the invokable TP is located.  
  
 With communication involving more than two TPs, the verification of a user identifier and password can be passed from one TP to another. Suppose that TP A invokes TP B, which requires security information, and TP B in turn invokes TP C, which also requires security information. Through **ALLOCATE** or **MC_ALLOCATE**, TP B can inform TP C that conversation security has already been verified.  
  
 For information about the registry or environment variables affecting conversation security, see [Configuring Invokable TPs](../core/configuring-invokable-tps1.md).
