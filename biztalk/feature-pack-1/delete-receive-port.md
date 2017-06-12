---
title: "Delete Receive port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f81dcd12-5e07-4549-8079-2fd1bde62b50
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# DELETE /ReceivePorts/{receivePortName}
## Delete Receive port


Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|receivePortName|{receivePortName}|ReceivePort Name|path|string|


Method  | Request URL
------------- | -------------
DELETE  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceivePorts/%7BreceivePortName%7D

Response Messages
---
|HTTP Status Code|Reason|Response Model|Headers|
|---|---|---|---|
|204|No Content|||

Response
---
| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X DELETE --header 'Accept: text/plain' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceivePorts/%7BreceivePortName%7D'|
| Response Body | Index (zero based) must be greater than or equal to zero and less than the size of the argument list.|
| Response Code | 500|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 08:17:44 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/plain; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "101",
  "expires": "-1"
}
```

