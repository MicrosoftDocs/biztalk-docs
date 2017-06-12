---
title: "Get TransactionSetAggregationReport application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 20d5e28f-36ce-4430-ae49-c4c5181fd3a4
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get TransactionSetAggregationReport: application/json
## Get TransactionSetAggregationReport

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/TransactionSetAggregationReports

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/plain' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/TransactionSetAggregationReports'|
| Response Body | Could not load file or assembly 'Microsoft.BizTalk.SnapIn.Framework, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified.|
| Response Code | 500|


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 08:29:10 GMT",
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
    "AgreementName": "string",
    "Direction": "string",
    "Id": "string",
    "MaxInterchangeDateTime": "2017-04-21T00:56:37.598Z",
    "MinInterchangeDateTime": "2017-04-21T00:56:37.598Z",
    "ReceiverPartyName": "string",
    "SenderPartyName": "string",
    "TransactionSetCount": 0,
    "TransactionSetId": "string"
  }
]

```
