---
title: "TP Name Not Unique; Local LU Alias Unique (SNA)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f425307-a8b5-4632-ade2-4ce1658112c1
caps.latest.revision: 3
---
# TP Name Not Unique; Local LU Alias Unique (SNA)
Another way to specify the intended system where the invokable TP will run is to give the same name to multiple invokable TPs, but associate each TP with a unique local LU alias. To do this, configure each invokable TP (through registry or environment variables) to use a unique local LU alias. Then set up the invoking TPs so that each one is routed not only to the correct TP name but also to the correct partner LU alias for the intended invokable TP.