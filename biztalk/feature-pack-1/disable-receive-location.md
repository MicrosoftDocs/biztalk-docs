---
title: "Disable receive location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 004b5ddb-95e4-4867-8272-d123b2ccecb9
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# PUT /ReceiveLocations/Disable/{receivePortName}/{receiveLocationName}
## Disable receive location


Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|receivePortName|{receivePortName}|Receive port name|path|string|
|receiveLocationName|{receiveLocationName}|Receive location name|path|string|

Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations/Disable/%7BreceivePortName%7D/%7BreceiveLocationName%7D

Response Messages
---
|HTTP Status Code|Reason|Response Model|Headers|
|---|---|---|---|
|204|No Content|||

Response
---
| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations/Disable/%7BreceivePortName%7D/%7BreceiveLocationName%7D'|
| Response Body | `{  "Message": "ReceivePort with name {receivePortName} does not exist." }`|
| Response Code | 404|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 05:45:20 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "69",
  "expires": "-1"
}
```

