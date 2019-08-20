---
title: "LUA Programmer&#39;s Security Guide2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a4b0e15-e557-4573-9cc8-5d21ca042cf5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# LUA Programmer&#39;s Security Guide
The following topics discuss security as it applies to the LUA section of the Host Integration Server SDK.  
  
## About LUA security for developers  
 LUA presents a simple API that enables programmatic control over the SNA messages. LUA has a simple structure, but exposes a complex data stream, that associated with SNA messages.  
  
 Since LUA is a low-level interface, the programmer must be especially vigilant on security issues.  
  
## Threats and mitigations for LUA  
 Programmers who use this feature should be aware of the following security practices and issues.  
  
### The data stream between Host Integration Server and the Mainframe is not encrypted.  
 LUA provides no encryption for the data stream between Host Integration Server and the Mainframe.