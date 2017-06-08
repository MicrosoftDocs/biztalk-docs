---
title: "Get all Orchestrations text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c1c698c4-e6a6-46c0-9c2e-bd120305eb4d
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get all Orchestrations: text/xml
## Get all Orchestrations

  Response Content Type: **text/xml**

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
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations'|
| Response Code | 200|

Response Body
---
```
<ArrayOfOrchestration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><Orchestration><FullName>AddDataToSQL.ProcessOrders</FullName><AssemblyName>OldOrdersReceive</AssemblyName><ApplicationName>OldOrdersReceive</ApplicationName><Description /><Status>Started</Status><Host>ProcessingHost</Host><InboundPorts><OrchestrationInboundPort><Name>ReceiveOrderFromFile</Name><Binding>Physical</Binding><ReceivePort>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0</ReceivePort><PortType>AddDataToSQL.ReceiveFileOrder</PortType></OrchestrationInboundPort></InboundPorts><OutboundPorts><OrchestrationOutboundPort><Name>SaveBackupOfOrder</Name><Binding>Logical</Binding><SendPort>BackupFile</SendPort><SendPortGroup /><PortType>AddDataToSQL.SaveBackupofOrder</PortType></OrchestrationOutboundPort><OrchestrationOutboundPort><Name>SendOrderToSQL</Name><Binding>Logical</Binding><SendPort>WcfSendPort_SqlAdapterBinding_TypedProcedures_dbo_Custom</SendPort><SendPortGroup /><PortType>AddDataToSQL.SendOrderToCRM</PortType></OrchestrationOutboundPort><OrchestrationOutboundPort><Name>SQLResponseMessage</Name><Binding>Logical</Binding><SendPort>ResponseSQL</SendPort><SendPortGroup /><PortType>AddDataToSQL.ResponseFromSQL</PortType></OrchestrationOutboundPort></OutboundPorts><UsedRoles /><ImplementedRoles /><InvokedOrchestrations /><Tracking><ServiceStartEnd>true</ServiceStartEnd><MessageSendReceive>true</MessageSendReceive><InboundMessageBody>false</InboundMessageBody><OutboundMessageBody>false</OutboundMessageBody><OrchestartionEvents>true</OrchestartionEvents><TrackPropertiesForIncomingMessages>false</TrackPropertiesForIncomingMessages><TrackPropertiesForOutgoingMessages>false</TrackPropertiesForOutgoingMessages></Tracking></Orchestration></ArrayOfOrchestration>
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 04:16:08 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1853",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <FullName>string</FullName>
  <AssemblyName>string</AssemblyName>
  <ApplicationName>string</ApplicationName>
  <Description>string</Description>
  <Status>string</Status>
  <Host>string</Host>
  <InboundPorts>
    <Name>string</Name>
    <Binding>string</Binding>
    <ReceivePort>string</ReceivePort>
    <PortType>string</PortType>
  </InboundPorts>
  <OutboundPorts>
    <Name>string</Name>
    <Binding>string</Binding>
    <SendPort>string</SendPort>
    <SendPortGroup>string</SendPortGroup>
    <PortType>string</PortType>
  </OutboundPorts>
  <UsedRoles>string</UsedRoles>
  <ImplementedRoles>string</ImplementedRoles>
  <InvokedOrchestrations>string</InvokedOrchestrations>
  <Tracking>
    <ServiceStartEnd>true</ServiceStartEnd>
    <MessageSendReceive>true</MessageSendReceive>
    <InboundMessageBody>true</InboundMessageBody>
    <OutboundMessageBody>true</OutboundMessageBody>
    <OrchestartionEvents>true</OrchestartionEvents>
    <TrackPropertiesForIncomingMessages>true</TrackPropertiesForIncomingMessages>
    <TrackPropertiesForOutgoingMessages>true</TrackPropertiesForOutgoingMessages>
  </Tracking>
\</Inline Model>
```