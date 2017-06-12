---
title: "Get hosts text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f418c37c-6e36-4f92-a9b4-b5806dd58812
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get hosts: text/json
## Get hosts

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Hosts

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Hosts'|
| Response Body | [{"Name":"SendHost","IsDefault":true,"NTGroupName":"BizTalk Application Users","Type":"InProcess","IsTrusted":false},{"Name":"BizTalkServerIsolatedHost","IsDefault":false,"NTGroupName":"BizTalk Isolated Host Users","Type":"Isolated","IsTrusted":false},{"Name":"ProcessingHost","IsDefault":false,"NTGroupName":"BizTalk Application Users","Type":"InProcess","IsTrusted":false},{"Name":"ReceiveHost","IsDefault":false,"NTGroupName":"BizTalk Application Users","Type":"InProcess","IsTrusted":false},{"Name":"TrackingHost","IsDefault":false,"NTGroupName":"BizTalk Application Users","Type":"InProcess","IsTrusted":false}]|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 01:34:37 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "616",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "IsDefault": true,
    "NTGroupName": "string",
    "Type": "string",
    "IsTrusted": true
  }
]
```
