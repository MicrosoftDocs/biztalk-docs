---
title: "Start Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 8f5c40c4-6213-4b68-9bff-d4c86f0ab93c
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# put  /Orchestrations/{applicationName}/{orchestrationName}/Start
## Start Orchestration


Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations/%7BapplicationName%7D/%7BorchestrationName%7D/Start

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations/%7BapplicationName%7D/%7BorchestrationName%7D/Start'|
| Response Code | 404|


Response Body
---
```
{
  "Message": "Application with name {applicationName} does not exists."
}
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 07:58:39 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "70",
  "expires": "-1"
}
```
Parameter  | Value  | Description  | Parameter Type  | Data Type
------------- | ------------- | ------------- | ------------- | -------------
**applicationName** | | **Application Name** | path | string
**orchestrationName** | | **Orchestration Name** | path | string

HTTP Status Code  | Reason  | Response Model  | Headers
------------- | ------------- | ------------- | -------------
204 | No Content|  |  | 

