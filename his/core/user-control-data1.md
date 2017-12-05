---
title: "User Control Data1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bfda01ad-f33f-4f37-99c1-8dfb043c99df
caps.latest.revision: 3
---
# User Control Data
For mapped conversations, the [MC_SEND_DATA](../core/mc-send-data2.md) verb and the receive verbs ([MC_RECEIVE_AND_POST](../core/mc-receive-and-post1.md), [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait1.md), and [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate1.md)) are modified to allow applications to send and receive data in user control data general data stream (GDS) variables instead of the regular application data GDS variables. The **MC_SEND_DATA** verb is modified as follows:  
  
-   A new parameter, **data_type**, is added. When **data_type** is set to AP_USER_CONTROL_DATA, the data is sent as user control data (GDS identifier 0x12F2). When it is set to AP_APPLICATION (the default), the data is sent as application data (GDS identifier 0x12FF). Note that the APPC library automatically creates the GDS header on behalf of the application for both AP_APPLICATION and AP_USER_CONTROL_DATA data records.  
  
-   The mapped conversation receive verbs are modified to allow applications to receive user control data by adding two new values for the **what_rcvd** parameter, as follows:  
  
     AP_USER_CONTROL_DATA_COMPLETE  
  
     AP_USER_CONTROL_DATA_INCOMPLETE