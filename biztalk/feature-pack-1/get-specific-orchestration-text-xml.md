---
title: "Get Specific Orchestration text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 60eb4761-8cc8-43bc-b74e-b18793f3fd7a
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Specific Orchestration: text/xml
## Get Specific Orchestration

  Response Content Type: **text/xml**

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
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations/%7BapplicationName%7D/%7BorchestrationName%7D'|
| Response Code | 404|

Response Body
---
```
<Error><Message>Application with name {applicationName} does not exists.</Message></Error>
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 07:28:59 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "90",
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
\<?xml version="1.0"?>
<Orchestration>
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
</Orchestration>
```