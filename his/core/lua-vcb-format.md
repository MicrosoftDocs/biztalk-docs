---
title: "LUA VCB Format1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c844def2-0911-4f09-8ef5-67fe7e5281c4
caps.latest.revision: 4
---
# LUA VCB Format
The logical unit application (LUA) verb control block (VCB) is called [LUA_VERB_RECORD](../core/lua-verb-record.md). It is a structure with two parts:  
  
-   A structure, [LUA_COMMON](../core/lua-common.md), which is used for all the LUA verbs.  
  
-   A union, [LUA_SPECIFIC](../core/lua-specific.md), which is used only by [RUI_BID](../Topic/RUI_BID2.md),[SLI_BID](../Topic/SLI_BID1.md),[SLI_OPEN](../core/sli-open.md), and [SLI_SEND](../Topic/SLI_SEND1.md).  
  
 This section contains:  
  
-   [LUA_VERB_RECORD](../core/lua-verb-record.md)  
  
-   [LUA_COMMON](../core/lua-common.md)  
  
-   [LUA_SPECIFIC](../core/lua-specific.md)