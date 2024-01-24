---
description: "Learn more about: User Control Data"
title: "User Control Data2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# User Control Data
For mapped conversations, the [MC_SEND_DATA](./mc-send-data1.md) verb and the receive verbs ([MC_RECEIVE_AND_POST](./mc-receive-and-post2.md), [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md), and [MC_RECEIVE_IMMEDIATE](./mc-receive-immediate2.md)) are modified to allow applications to send and receive data in user control data general data stream (GDS) variables instead of the regular application data GDS variables. The **MC_SEND_DATA** verb is modified as follows:  
  
-   A new parameter, **data_type**, is added. When **data_type** is set to AP_USER_CONTROL_DATA, the data is sent as user control data (GDS identifier 0x12F2). When it is set to AP_APPLICATION (the default), the data is sent as application data (GDS identifier 0x12FF). Note that the APPC library automatically creates the GDS header on behalf of the application for both AP_APPLICATION and AP_USER_CONTROL_DATA data records.  
  
-   The mapped conversation receive verbs are modified to allow applications to receive user control data by adding two new values for the **what_rcvd** parameter, as follows:  
  
     AP_USER_CONTROL_DATA_COMPLETE  
  
     AP_USER_CONTROL_DATA_INCOMPLETE
