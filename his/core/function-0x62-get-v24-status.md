---
title: "Function 0x62: Get V24 Status1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7416811-b67a-4e1d-85e2-65e8718a1c44
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Function 0x62: Get V24 Status
The SNALink calls this function to read the current state of the modem interface lines. No parameter or data packet is passed. This request causes the driver to update the Input V.24 Status field in the driver interface record.