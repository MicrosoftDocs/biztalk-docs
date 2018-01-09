---
title: "TP Name Not Unique; Local LU Alias Unspecified (SNA)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 648a3e0f-2135-44f5-857d-3ab58bb3b0cd
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TP Name Not Unique; Local LU Alias Unspecified (SNA)
If it does not matter on which system an invokable TP runs, use the same name for multiple invokable TPs and do not specify an LU alias in the registry or environment variables for the TPs. In this situation, there are no associated LU aliases in the list of available invokable TP names on a Host Integration Server. Thus, a request received from an invoking TP cannot cause a mismatch on the LU alias, and will match according to the TP name.  
  
 In this situation, if you set the **DloadMatchLocalFirst** registry entry to NO, Host Integration Server randomly routes the request to one of the available TPs. This spreads the processing load among multiple systems and provides hot backup (the ability to take systems online and offline without disrupting service).