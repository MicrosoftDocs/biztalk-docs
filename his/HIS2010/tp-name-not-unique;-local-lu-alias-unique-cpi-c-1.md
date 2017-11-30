---
title: "TP Name Not Unique; Local LU Alias Unique (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea5c19ad-cf4b-45db-bbd3-a6dd1b7fa212
caps.latest.revision: 3
---
# TP Name Not Unique; Local LU Alias Unique (CPI-C)
Another way to specify the intended system where the invokable transaction program (TP) will run is to give the same name to multiple invokable TPs, but associate each TP with a unique local logical unit (LU) alias. To do this, configure each invokable TP (through registry or environment variables) to use a unique local LU alias. Then set up the invoking TPs so that each one is routed not only to the correct TP name but also to the correct partner LU alias for the intended invokable TP.