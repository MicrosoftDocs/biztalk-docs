---
title: "TP Name Not Unique; Local LU Alias Unique (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00f22a20-85d4-463a-8da5-54bbe447363e
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# TP Name Not Unique; Local LU Alias Unique (CPI-C)
Another way to specify the intended system where the invokable transaction program (TP) will run is to give the same name to multiple invokable TPs, but associate each TP with a unique local logical unit (LU) alias. To do this, configure each invokable TP (through registry or environment variables) to use a unique local LU alias. Then set up the invoking TPs so that each one is routed not only to the correct TP name but also to the correct partner LU alias for the intended invokable TP.