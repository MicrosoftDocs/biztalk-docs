---
description: "Learn more about: Recovering from SESSION_FAILURE"
title: "Recovering from SESSION_FAILURE2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d5624d8-6220-4565-860d-dab05cdabe91
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Recovering from SESSION_FAILURE
If the [SLI_OPEN](../core/sli-open2.md) completes with the primary return code of SESSION_FAILURE, the Windows logical unit application (LUA) interface enables you to reissue **SLI_OPEN** without issuing [SLI_CLOSE](../core/sli-close1.md).
