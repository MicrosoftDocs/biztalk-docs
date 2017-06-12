---
title: "Set primary receive location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: e59e83b3-9f5f-4fea-9b17-0eaad69d2f0b
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# PUT /ReceiveLocations/SetPrimary/{receivePortName}/{receiveLocationName}
## Set primary receive location


Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|receivePortName|{receivePortName}|Receive port name|path|string|
|receiveLocationName|{receiveLocationName}|Receive location name|path|string|

Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations/SetPrimary/%7BreceivePortName%7D/%7BreceiveLocationName%7D

Response Messages
---
|HTTP Status Code|Reason|Response Model|Headers|
|---|---|---|---|
|204|No Content|||

Response
---
| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations/SetPrimary/%7BreceivePortName%7D/%7BreceiveLocationName%7D'|
| Response Body | `{  "Message": "ReceivePort with name {receivePortName} does not exist." }`|
| Response Code | 404|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 06:09:37 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "69",
  "expires": "-1"
}
```

