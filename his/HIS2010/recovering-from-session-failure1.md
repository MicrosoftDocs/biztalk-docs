---
title: "Recovering from SESSION_FAILURE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec028048-052a-4076-92fc-321c54ca8e88
caps.latest.revision: 3
---
# Recovering from SESSION_FAILURE
If the [SLI_OPEN](../HIS2010/sli-open1.md) completes with the primary return code of SESSION_FAILURE, the Windows logical unit application (LUA) interface enables you to reissue **SLI_OPEN** without issuing [SLI_CLOSE](../HIS2010/sli-close2.md).