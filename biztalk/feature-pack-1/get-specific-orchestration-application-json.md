---
title: "Get Specific Orchestration application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 41827175-cfa7-44fe-be4b-c67efa6185be
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Specific Orchestration: application/json
## Get Specific Orchestration

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations/%7BapplicationName%7D/%7BorchestrationName%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations/%7BapplicationName%7D/%7BorchestrationName%7D'|
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
  "date": "Mon, 24 Apr 2017 07:08:41 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "70",
  "expires": "-1"
}
```

Parameters
---
Parameter  | Value  | Description  | Parameter Type  | Data Type
------------- | ------------- | ------------- | ------------- | -------------
**applicationName** | | **Name of application** | path | string
**orchestrationName** | | **Name of Orchestration** | path | string

Example Value
---

```
{
  "FullName": "string",
  "AssemblyName": "string",
  "ApplicationName": "string",
  "Description": "string",
  "Status": "string",
  "Host": "string",
  "InboundPorts": [
    {
      "Name": "string",
      "Binding": "string",
      "ReceivePort": "string",
      "PortType": "string"
    }
  ],
  "OutboundPorts": [
    {
      "Name": "string",
      "Binding": "string",
      "SendPort": "string",
      "SendPortGroup": "string",
      "PortType": "string"
    }
  ],
  "UsedRoles": [
    "string"
  ],
  "ImplementedRoles": [
    "string"
  ],
  "InvokedOrchestrations": [
    "string"
  ],
  "Tracking": {
    "ServiceStartEnd": true,
    "MessageSendReceive": true,
    "InboundMessageBody": true,
    "OutboundMessageBody": true,
    "OrchestartionEvents": true,
    "TrackPropertiesForIncomingMessages": true,
    "TrackPropertiesForOutgoingMessages": true
  }
}

```
