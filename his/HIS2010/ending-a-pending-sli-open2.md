---
title: "Ending a Pending SLI_OPEN2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd66265a-470b-4e64-89d3-fe0cb90552b0
caps.latest.revision: 3
---
# Ending a Pending SLI_OPEN
To end a pending [SLI_OPEN](../HIS2010/sli-open1.md), issue [SLI_CLOSE](../HIS2010/sli-close2.md) with **lua_flag2.close_abend** set to ON.