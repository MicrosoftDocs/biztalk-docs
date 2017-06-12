---
title: "Get Receive Ports application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: e1d8382c-893c-4de1-a2b9-a30802b5255b
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Receive Ports: application/json
## Get Receive Ports

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceivePorts

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceivePorts'|
| Response Code | 200|

Response Body
---
```
[
  {
    "Name": "OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0",
    "Description": null,
    "IsTwoWay": false,
    "ApplicationName": "OldOrdersReceive",
    "CustomData": null,
    "InboundTransforms": [],
    "OutboundTransforms": [],
    "Tracking": {
      "Body": {
        "BeforeSendPipeline": false,
        "AfterSendPipeline": false,
        "BeforeReceivePipeline": false,
        "AfterReceivePipeline": false
      },
      "Property": {
        "BeforeSendPipeline": false,
        "AfterSendPipeline": false,
        "BeforeReceivePipeline": false,
        "AfterReceivePipeline": false
      }
    },
    "ReceiveLocations": [
      "OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation"
    ],
    "PrimaryReceiveLocation": "OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation"
  }
]
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 06:48:02 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "761",
  "expires": "-1"
}
```

Example Value
---

```
[
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
]
```