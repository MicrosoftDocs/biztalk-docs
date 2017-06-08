---
title: "Get AS2StatusRecords text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c90de223-eb05-4dc2-845b-257f8eb1b4ea
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get AS2StatusRecords: text/json
## Get AS2StatusRecords

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/AS2StatusRecords

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/plain' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/AS2StatusRecords'|
| Response Body | Could not load file or assembly 'Microsoft.BizTalk.SnapIn.Framework, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified.|
| Response Code | 500|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 09:19:09 GMT",
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
    "AgreementName": "string",
    "AS2From": "string",
    "AS2PartyRole": "string",
    "AS2To": "string",
    "DaysToCheckDuplicate": "string",
    "Filename": "string",
    "InterchangeControlNo": "string",
    "IsAS2MessageDuplicate": "string",
    "IsReliableMessagingEnabled": "string",
    "MdnProcessingStatus": "string",
    "MessageDateTime": "2017-04-21T00:56:37.617Z",
    "MessageEncryptionType": "string",
    "MessageID": "string",
    "MessageSignatureType": "string",
    "ReceiverPartyName": "string",
    "SenderPartyName": "string",
    "TimeCreated": "2017-04-21T00:56:37.617Z"
  }
]
```
