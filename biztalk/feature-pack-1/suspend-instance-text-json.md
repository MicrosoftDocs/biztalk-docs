---
title: "Suspend instance text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 564b424c-52cc-447c-8146-dbaf98df56a3
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Suspend instance: text/json
## Suspend instance

  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Instances/Suspend/%7BinstanceId%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Instances/Suspend/%7BinstanceId%7D'|
| Response Code | 400|

Parameters
---

Parameter  | Value  | Description  | Parameter Type  | Data Type
------------- | ------------- | ------------- | ------------- | -------------
**instanceId** | | **instance Id** | path | string

Response Body
---
```
{"Message":"Please provide a valid instance Id"}
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 05:31:32 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "48",
  "expires": "-1"
}
```

Example Value
---

```
{}

```
