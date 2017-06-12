---
title: "Update Orchestration text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 13ea5b82-fcfb-4c84-9b40-f0440cc30fc4
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Orchestration: text/xml
## Update Orchestration. 
Allows us to Bind/Unbind Ports, Host and Change Tracking Options

  Response Content Type: **text/xml**



Method  | Request URL
------------- | -------------
PUT  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Content-Type: text/xml' --header 'Accept: text/plain' -d 'Orchestrations' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Orchestrations'|
| Response Code | 500|

Response Body
---
```
Object reference not set to an instance of an object.
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Tue, 25 Apr 2017 00:40:57 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/plain; charset=utf-8",
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

Response Messages
---

HTTP Status Code  | Reason  | Response Model  | Headers
------------- | ------------- | ------------- | -------------
204 | No Content|  |  | 
