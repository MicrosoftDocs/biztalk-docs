---
title: "Update Receive port application x www form urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: bb4c89bc-6781-44a6-bd2b-703466b6f0c6
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Receive port: application/x-www-form-urlencoded
## Update Receive Port


Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|receiveport|(required)|Receive port details|body|Example Value|

Example Value
---
```
{
  "Name": "string",
  "Description": "string",
  "IsTwoWay": true,
  "ApplicationName": "string",
  "CustomData": "string",
  "InboundTransforms": [
    "string"
  ],
  "OutboundTransforms": [
    "string"
  ],
  "Tracking": {
    "Body": {
      "BeforeSendPipeline": true,
      "AfterSendPipeline": true,
      "BeforeReceivePipeline": true,
      "AfterReceivePipeline": true
    },
    "Property": {
      "BeforeSendPipeline": true,
      "AfterSendPipeline": true,
      "BeforeReceivePipeline": true,
      "AfterReceivePipeline": true
    }
  },
  "ReceiveLocations": [
    "string"
  ],
  "PrimaryReceiveLocation": "string"
}
```


Response Messages
---
|HTTP Status Code|Reason|Response Model|Headers|
|---|---|---|---|
|204|No Content|||



