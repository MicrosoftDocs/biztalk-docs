---
title: "Get SendportGroups text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 21da2b5b-f7e8-4649-bbd8-710b7c3e19f8
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get SendportGroups: text/json
## Get SendportGroups

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  |http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/SendPortGroups |

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/SendPortGroups' |
| Response Code | 200|

## Response Body


```
[{"Name":"SendPortGroup1","SendPorts":["BackupFile","ResponseSQL"],"CustomData":null,"Filter":"<?xml version=\"1.0\" encoding=\"utf-16\"?>\r\n<Filter xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\" xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\">\r\n  <Group>\r\n    <Statement Property=\"BTS.ReceivePortName\" Operator=\"0\" Value=\"RecLoc\" />\r\n  </Group>\r\n</Filter>","Status":"Bound","ApplicationName":"OldOrdersReceive","Description":null}]
```



Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 01:04:34 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "455",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "SendPorts": [
      "string"
    ],
    "CustomData": "string",
    "Filter": "string",
    "Status": "string",
    "ApplicationName": "string",
    "Description": "string"
  }
]

```
