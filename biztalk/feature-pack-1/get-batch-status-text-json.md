---
title: "Get batch status text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 2a28b70a-f5f7-450d-a7d3-a4551c9d0ae7
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get batch status: text/json
## Get batch status

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Batches/Status/%7BdestinationPartyName%7D/%7BbatchName%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/plain' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Batches/Status/%7BdestinationPartyName%7D/%7BbatchName%7D'|
| Response Body | Could not find stored procedure 'bts_GetBatchStatusRecords'.|
| Response Code | 500|

Parameters
---
Parameter  | Value  | Description  | Parameter Type  | Data Type
------------- | ------------- | ------------- | ------------- | -------------
**destinationPartyName** | | **The destination of the oneway agreement.** | path | string
**batchName** | | **The agreement name.** | path | string

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 01:42:07 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/plain; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "60",
  "expires": "-1"
}
```

