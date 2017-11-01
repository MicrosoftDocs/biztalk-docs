---
title: "LUA Verb Control Blocks2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 857d54d6-74bb-4643-820f-693d218fcc1f
caps.latest.revision: 3
---
# LUA Verb Control Blocks
When an application issues a Microsoft® Windows® logical unit application (LUA) verb, the verb is coded within the application as a precisely defined verb control block (VCB). The total length of this VCB is variable and is defined by **lua_verb_length**.  
  
 This section defines the structure of individual Windows LUA VCBs.  
  
 This section contains:  
  
-   [Common Structure of LUA VCBs](../core/common-structure-of-lua-vcbs.md)  
  
-   [Values for lua_message_type](../core/values-for-lua-message-type.md)  
  
-   [Command-Specific Structure of LUA VCBs](../core/command-specific-structure-of-lua-vcbs.md)