---
title: "Update Orchestration application x www form urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: fbed9721-3573-46cf-aa29-53ce78833a44
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Orchestration: application/x-www-form-urlencoded
## Update Orchestration. 
Allows us to Bind/Unbind Ports, Host and Change Tracking Options

  Response Content Type: **application/x-www-form-urlencoded**


Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' -d 'Orchestrations' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations'|
| Response Code | 404|

Response Body
---
```
{
  "Message": "Application with name  does not exists."
}
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Tue, 25 Apr 2017 00:43:56 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "53",
  "expires": "-1"
}
```
Parameters
---
Parameter  | Value  | Description  | Parameter Type  | Data Type
------------- | ------------- | ------------- | ------------- | -------------
**orchestration** | | **Updated Orchestration Properties** | body | Example Value

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

Response Messages
---

HTTP Status Code  | Reason  | Response Model  | Headers
------------- | ------------- | ------------- | -------------
204 | No Content|  |  | 
