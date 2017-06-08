---
title: "Get Protocol types application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: af0a0113-7c79-4e7e-b7e2-03de348511fe
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Protocol types: application/xml
## Get Protocol types

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ProtocolTypes

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ProtocolTypes'|
| Response Code | 200|

Response Body
---
```
\<ArrayOfProtocolType xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <ProtocolType>
    <Name>HTTP</Name>
    <Capabilities>SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>SOAP</Name>
    <Capabilities>SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>FILE</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>Windows SharePoint Services</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, InitOutboundProtocolContext, InitInboundProtocolContext, InitReceiveLocationContext, InitTransmitLocationContext</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>SMTP</Name>
    <Capabilities>SupportsSend</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>SQL</Name>
    <Capabilities>81163</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>FTP</Name>
    <Capabilities>80907</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>POP3</Name>
    <Capabilities>71689</Capabilities>
  </ProtocolType>
  <ProtocolType>
    <Name>MSMQ</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSolicitResponse, InitOutboundProtocolContext, InitReceiveLocationContext, InitTransmitLocationContext</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>MQSeries</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSolicitResponse, InitOutboundProtocolContext, InitInboundProtocolContext, InitReceiveLocationContext, InitTransmitLocationContext</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-BasicHttp</Name>
    <Capabilities>SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-Custom</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-CustomIsolated</Name>
    <Capabilities>SupportsReceive, SupportsRequestResponse, SupportsSoap</Capabilities>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-NetMsmq</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-NetNamedPipe</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-NetTcp</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-WSHttp</Name>
    <Capabilities>SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-WebHttp</Name>
    <Capabilities>SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>SB-Messaging</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-BasicHttpRelay</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-NetTcpRelay</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>SFTP</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
  <ProtocolType>
    <Name>WCF-SQL</Name>
    <Capabilities>SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSolicitResponse, SupportsSoap</Capabilities>
    <DefaultSendHandler>SendHost</DefaultSendHandler>
  </ProtocolType>
</ArrayOfProtocolType>
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 02:48:29 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "4944",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <Name>string</Name>
  <Capabilities>string</Capabilities>
  <DefaultSendHandler>string</DefaultSendHandler>
\</Inline Model>
```