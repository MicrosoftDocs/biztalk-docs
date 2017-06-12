---
title: "Get Batches text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 98084dfa-3dcc-411b-b8e6-a37fa083917e
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Batches: text/json
## Get Batches

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Batches

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/plain' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Batches'|
| Response Body | Could not load file or assembly 'Microsoft.BizTalk.SnapIn.Framework, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified.|
| Response Code | 500|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 09:28:39 GMT",
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
    "Name": "string",
    "BatchStatus": "string",
    "BatchName": "string",
    "DestinationPartyName": "string",
    "ActivationTime": "2017-04-21T00:56:37.622Z",
    "BatchOccurrenceCount": 0,
    "EdiEncodingType": "string",
    "BatchType": "string",
    "BatchTarget": "string",
    "BatchElementCount": 0,
    "RejectedBatchElementCount": 0,
    "BatchSize": "string",
    "LastBatchAction": "string",
    "InterchangeControlNo": "string",
    "InterchangeDateTime": "2017-04-21T00:56:37.622Z",
    "AgreementName": "string"
  }
]
```
