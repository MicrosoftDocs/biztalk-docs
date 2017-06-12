---
title: "Get InterchangeStatusRecords text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 6a313171-a3ff-4e1e-bf1c-60078e522ac5
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get InterchangeStatusRecords: text/json
## Get InterchangeStatusRecords

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/InterchangeStatusRecords

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/plain' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/InterchangeStatusRecords'|
| Response Body | Could not load file or assembly 'Microsoft.BizTalk.SnapIn.Framework, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified.|
| Response Code | 500|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 08:54:41 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/plain; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "206",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Id": "string",
    "ReceiverPartyName": "string",
    "SenderPartyName": "string",
    "ReceiverPartyAlias": "string",
    "SenderPartyAlias": "string",
    "InterchangeControlNo": "string",
    "Direction": "string",
    "InterchangeDateTime": "2017-04-21T00:56:37.609Z",
    "EdiMessageType": "string",
    "IsaStatusCode": "string",
    "GroupCount": {},
    "PortID": {},
    "TsCorrelationId": {},
    "AgreementName": {}
  }
]
```
