---
title: "LUA VCB Format1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c844def2-0911-4f09-8ef5-67fe7e5281c4
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# LUA VCB Format
The logical unit application (LUA) verb control block (VCB) is called [LUA_VERB_RECORD](../core/lua-verb-record2.md). It is a structure with two parts:  

- A structure, [LUA_COMMON](../core/lua-common1.md), which is used for all the LUA verbs.  

- A union, [LUA_SPECIFIC](../core/lua-specific1.md), which is used only by [RUI_BID](./rui-bid1.md),[SLI_BID](./sli-bid2.md),[SLI_OPEN](../core/sli-open2.md), and [SLI_SEND](./sli-send2.md).  

  This section contains:  

- [LUA_VERB_RECORD](../core/lua-verb-record2.md)  

- [LUA_COMMON](../core/lua-common1.md)  

- [LUA_SPECIFIC](../core/lua-specific1.md)
