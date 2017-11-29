---
title: "User Control Data2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 667870f5-3690-4ad7-9b9e-82f917670ef2
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# User Control Data
For mapped conversations, the [MC_SEND_DATA](../Topic/MC_SEND_DATA2.md) verb and the receive verbs ([MC_RECEIVE_AND_POST](../Topic/MC_RECEIVE_AND_POST1.md), [MC_RECEIVE_AND_WAIT](../Topic/MC_RECEIVE_AND_WAIT1.md), and [MC_RECEIVE_IMMEDIATE](../Topic/MC_RECEIVE_IMMEDIATE1.md)) are modified to allow applications to send and receive data in user control data general data stream (GDS) variables instead of the regular application data GDS variables. The **MC_SEND_DATA** verb is modified as follows:  
  
-   A new parameter, **data_type**, is added. When **data_type** is set to AP_USER_CONTROL_DATA, the data is sent as user control data (GDS identifier 0x12F2). When it is set to AP_APPLICATION (the default), the data is sent as application data (GDS identifier 0x12FF). Note that the APPC library automatically creates the GDS header on behalf of the application for both AP_APPLICATION and AP_USER_CONTROL_DATA data records.  
  
-   The mapped conversation receive verbs are modified to allow applications to receive user control data by adding two new values for the **what_rcvd** parameter, as follows:  
  
     AP_USER_CONTROL_DATA_COMPLETE  
  
     AP_USER_CONTROL_DATA_INCOMPLETE