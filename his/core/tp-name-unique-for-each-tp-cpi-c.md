---
title: "TP Name Unique for Each TP (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62066043-a24c-4b1b-9df0-f667069636ab
caps.latest.revision: 3
---
# TP Name Unique for Each TP (CPI-C)
One way to specify the intended system where the invokable transaction program (TP) will run is to use a unique TP name for each invokable TP. In this arrangement, the invoking TP identifies the intended invokable TP (and system) simply by naming the TP. This makes it unnecessary for an invokable TP to specify any logical unit (LU) alias in registry or environment variables.