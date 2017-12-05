---
title: "LUA VCB Format2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f6232f3-1346-4765-9051-c88f7d21f769
caps.latest.revision: 3
---
# LUA VCB Format
The logical unit application (LUA) verb control block (VCB) is called [LUA_VERB_RECORD](../core/lua-verb-record1.md). It is a structure with two parts:  
  
-   A structure, [LUA_COMMON](../core/lua-common2.md), which is used for all the LUA verbs.  
  
-   A union, [LUA_SPECIFIC](../core/lua-specific2.md), which is used only by [RUI_BID](../core/rui-bid2.md),[SLI_BID](../core/sli-bid1.md),[SLI_OPEN](../core/sli-open1.md), and [SLI_SEND](../core/sli-send1.md).  
  
 This section contains:  
  
-   [LUA_VERB_RECORD](../core/lua-verb-record1.md)  
  
-   [LUA_COMMON](../core/lua-common2.md)  
  
-   [LUA_SPECIFIC](../core/lua-specific2.md)