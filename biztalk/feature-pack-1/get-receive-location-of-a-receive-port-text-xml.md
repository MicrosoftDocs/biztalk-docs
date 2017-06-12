---
title: "Get receive location of a receive port text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 819fbb69-1dd4-42ef-a8d9-ffee2fca39f6
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get receive location of a receive port: text/xml
## Get receive location of a receive port

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|receivePortName|{receivePortName}|Receive port name|path|string|
|receiveLocationName|{receiveLocationName}|Receive location name|path|string|

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations/%7BreceivePortName%7D/%7BreceiveLocationName%7D

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations/%7BreceivePortName%7D/%7BreceiveLocationName%7D'|
| Response Body | `<Error><Message>ReceivePort with name {receivePortName} does not exist.</Message></Error>` |
| Response Code | 404|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 08:00:46 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "89",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<ReceiveLocation>
  <Name>string</Name>
  <Description>string</Description>
  <ReceivePortName>string</ReceivePortName>
  <Enable>true</Enable>
  <IsPrimary>true</IsPrimary>
  <Address>string</Address>
  <PublicAddress>string</PublicAddress>
  <TransportType>string</TransportType>
  <TransportTypeData>string</TransportTypeData>
  <ReceiveHandler>string</ReceiveHandler>
  <CustomData>string</CustomData>
  <ReceivePipeline>string</ReceivePipeline>
  <ReceivePipelineData>string</ReceivePipelineData>
  <SendPipeline>string</SendPipeline>
  <SendPipelineData>string</SendPipelineData>
  <Schedule>
    <StartDate>1970-01-01T00:00:00.001Z</StartDate>
    <StartDateEnabled>true</StartDateEnabled>
    <EndDate>1970-01-01T00:00:00.001Z</EndDate>
    <EndDateEnabled>true</EndDateEnabled>
    <ServiceWindowEnabled>true</ServiceWindowEnabled>
    <FromTime>1970-01-01T00:00:00.001Z</FromTime>
    <ToTime>1970-01-01T00:00:00.001Z</ToTime>
  </Schedule>
  <EncryptionCert>
    <CommonName>string</CommonName>
    <Thumbprint>string</Thumbprint>
  </EncryptionCert>
  <FragmentMessages>string</FragmentMessages>
</ReceiveLocation>
```
