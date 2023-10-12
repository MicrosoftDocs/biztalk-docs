---
description: "Learn more about: TP Name Not Unique; Local LU Alias Unspecified (CPI-C)"
title: "TP Name Not Unique; Local LU Alias Unspecified (CPI-C)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TP Name Not Unique; Local LU Alias Unspecified (CPI-C)
If it does not matter on which system an invokable transaction program (TP) runs, use the same name for multiple invokable TPs and do not specify a logical unit (LU) alias in the registry or environment variables for the TPs. In this situation, there are no associated LU aliases in the list of available invokable TP names on a computer running Host Integration Server. Thus, a request received from an invoking TP cannot cause a mismatch on the LU alias, and will match according to the TP name.  
  
 In this situation, if you set the **DloadMatchLocalFirst** registry entry to NO, the SNA service randomly routes the request to one of the available TPs. This spreads the processing load among multiple systems and provides hot backup (the ability to take systems online and offline without disrupting service).
