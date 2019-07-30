---
title: "Ending a Pending SLI_OPEN1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3c7a921-97ac-468a-b3bd-723e02d2bb76
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Ending a Pending SLI_OPEN
To end a pending [SLI_OPEN](../core/sli-open2.md), issue [SLI_CLOSE](../core/sli-close1.md) with **lua_flag1.close_abend** set to ON.