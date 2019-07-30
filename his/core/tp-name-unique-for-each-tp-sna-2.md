---
title: "TP Name Unique for Each TP (SNA)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 154492cd-de16-4505-a5cc-ad85b242e7d1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# TP Name Unique for Each TP (SNA)
One way to specify the intended system where the invokable TP will run is to use a unique TP name for each invokable TP. In this arrangement, the invoking TP identifies the intended invokable TP (and system) simply by naming the TP. This makes it unnecessary for an invokable TP to specify any LU alias in registry or environment variables.