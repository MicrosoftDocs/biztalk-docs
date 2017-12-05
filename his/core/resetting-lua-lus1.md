---
title: "Resetting LUA LUs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb7a1601-6424-41f7-ac2c-8f4c0bbb8d82
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Resetting LUA LUs
Microsoft® Host Integration Server provides a facility for resetting logical unit application (LUA) LUs or forcing off LUA applications, which is useful if an application has become deadlocked or is looping.  
  
 The NetView command **deactivate-oldlu** can also be used to reset an LUA LU. These facilities interact with the LUA application as described in the following paragraphs.  
  
 When an LUA LU is reset through Host Integration Server or by using the **deactivate-oldlu** command, Host Integration Server sends an UNBIND message to the application (as though the host had issued it).  
  
 The UNBIND message sent to the application is 0x32 0x0E, indicating a recoverable LU failure, and is returned to the application on a subsequent [RUI_READ](../core/rui-read1.md). The LU session is terminated, but the system services control point (SSCP) session remains active. (The LU is returned to the same state as if [RUI_INIT](../core/rui-init2.md) has just completed.)