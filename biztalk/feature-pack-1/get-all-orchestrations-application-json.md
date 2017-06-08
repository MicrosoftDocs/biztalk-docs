---
title: "Get all Orchestrations application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 552fd29b-9c48-4dbc-b0f0-3c0059aa0d54
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get all Orchestrations: application/json
## Get all Orchestrations

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations'|
| Response Code | 200|


Response Body
---
```
[
  {
    "FullName": "AddDataToSQL.ProcessOrders",
    "AssemblyName": "OldOrdersReceive",
    "ApplicationName": "OldOrdersReceive",
    "Description": "",
    "Status": "Started",
    "Host": "ProcessingHost",
    "InboundPorts": [
      {
        "Name": "ReceiveOrderFromFile",
        "Binding": "Physical",
        "ReceivePort": "OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0",
        "PortType": "AddDataToSQL.ReceiveFileOrder"
      }
    ],
    "OutboundPorts": [
      {
        "Name": "SaveBackupOfOrder",
        "Binding": "Logical",
        "SendPort": "BackupFile",
        "SendPortGroup": "",
        "PortType": "AddDataToSQL.SaveBackupofOrder"
      },
      {
        "Name": "SendOrderToSQL",
        "Binding": "Logical",
        "SendPort": "WcfSendPort_SqlAdapterBinding_TypedProcedures_dbo_Custom",
        "SendPortGroup": "",
        "PortType": "AddDataToSQL.SendOrderToCRM"
      },
      {
        "Name": "SQLResponseMessage",
        "Binding": "Logical",
        "SendPort": "ResponseSQL",
        "SendPortGroup": "",
        "PortType": "AddDataToSQL.ResponseFromSQL"
      }
    ],
    "UsedRoles": [],
    "ImplementedRoles": [],
    "InvokedOrchestrations": [],
    "Tracking": {
      "ServiceStartEnd": true,
      "MessageSendReceive": true,
      "InboundMessageBody": false,
      "OutboundMessageBody": false,
      "OrchestartionEvents": true,
      "TrackPropertiesForIncomingMessages": false,
      "TrackPropertiesForOutgoingMessages": false
    }
  }
]
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 03:21:18 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1153",
  "expires": "-1"
}
```

Example Value
---

```
[
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
]

```
