---
title: "Get Protocol types text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ec1fb2c6-b8e1-46a2-9d5d-aecf1da53d3f
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Protocol types: text/json
## Get Protocol types

  Response Content Type: **text/json**

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
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ProtocolTypes'|
| Response Body | ``` [{"Name":"HTTP","Capabilities":"SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse","DefaultSendHandler":"SendHost"},{"Name":"SOAP","Capabilities":"SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"FILE","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable","DefaultSendHandler":"SendHost"},{"Name":"Windows SharePoint Services","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, InitOutboundProtocolContext, InitInboundProtocolContext, InitReceiveLocationContext, InitTransmitLocationContext","DefaultSendHandler":"SendHost"},{"Name":"SMTP","Capabilities":"SupportsSend","DefaultSendHandler":"SendHost"},{"Name":"SQL","Capabilities":"81163","DefaultSendHandler":"SendHost"},{"Name":"FTP","Capabilities":"80907","DefaultSendHandler":"SendHost"},{"Name":"POP3","Capabilities":"71689","DefaultSendHandler":null},{"Name":"MSMQ","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSolicitResponse, InitOutboundProtocolContext, InitReceiveLocationContext, InitTransmitLocationContext","DefaultSendHandler":"SendHost"},{"Name":"MQSeries","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSolicitResponse, InitOutboundProtocolContext, InitInboundProtocolContext, InitReceiveLocationContext, InitTransmitLocationContext","DefaultSendHandler":"SendHost"},{"Name":"WCF-BasicHttp","Capabilities":"SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-Custom","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-CustomIsolated","Capabilities":"SupportsReceive, SupportsRequestResponse, SupportsSoap","DefaultSendHandler":null},{"Name":"WCF-NetMsmq","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-NetNamedPipe","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-NetTcp","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-WSHttp","Capabilities":"SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-WebHttp","Capabilities":"SupportsReceive, SupportsSend, SupportsRequestResponse, SupportsSolicitResponse","DefaultSendHandler":"SendHost"},{"Name":"SB-Messaging","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-BasicHttpRelay","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-NetTcpRelay","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsRequestResponse, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"SFTP","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSoap","DefaultSendHandler":"SendHost"},{"Name":"WCF-SQL","Capabilities":"SupportsReceive, SupportsSend, ReceiveIsCreatable, SupportsSolicitResponse, SupportsSoap","DefaultSendHandler":"SendHost"}] ```|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 02:34:48 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "3555",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "Capabilities": "string",
    "DefaultSendHandler": "string"
  }
]
```