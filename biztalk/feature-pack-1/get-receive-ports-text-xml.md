---
title: "Get Receive Ports text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 7e0922ac-971d-41b8-9d69-7026fb84003c
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Receive Ports: text/xml
## Get Receive Ports

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceivePorts

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: text/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceivePorts'|
| Response Body| `<ArrayOfReceivePort xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><ReceivePort><Name>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0</Name><IsTwoWay>false</IsTwoWay><ApplicationName>OldOrdersReceive</ApplicationName><InboundTransforms /><OutboundTransforms /><Tracking><Body><BeforeSendPipeline>false</BeforeSendPipeline><AfterSendPipeline>false</AfterSendPipeline><BeforeReceivePipeline>false</BeforeReceivePipeline><AfterReceivePipeline>false</AfterReceivePipeline></Body><Property><BeforeSendPipeline>false</BeforeSendPipeline><AfterSendPipeline>false</AfterSendPipeline><BeforeReceivePipeline>false</BeforeReceivePipeline><AfterReceivePipeline>false</AfterReceivePipeline></Property></Tracking><ReceiveLocations><string>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation</string></ReceiveLocations><PrimaryReceiveLocation>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation</PrimaryReceiveLocation></ReceivePort></ArrayOfReceivePort>`|
| Response Code | 200|

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 08:13:37 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1141",
  "expires": "-1"
}
```

Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <Name>string</Name>
  <Description>string</Description>
  <IsTwoWay>true</IsTwoWay>
  <ApplicationName>string</ApplicationName>
  <CustomData>string</CustomData>
  <InboundTransforms>string</InboundTransforms>
  <OutboundTransforms>string</OutboundTransforms>
  <Tracking>
    <Body>
      <BeforeSendPipeline>true</BeforeSendPipeline>
      <AfterSendPipeline>true</AfterSendPipeline>
      <BeforeReceivePipeline>true</BeforeReceivePipeline>
      <AfterReceivePipeline>true</AfterReceivePipeline>
    </Body>
    <Property>
      <BeforeSendPipeline>true</BeforeSendPipeline>
      <AfterSendPipeline>true</AfterSendPipeline>
      <BeforeReceivePipeline>true</BeforeReceivePipeline>
      <AfterReceivePipeline>true</AfterReceivePipeline>
    </Property>
  </Tracking>
  <ReceiveLocations>string</ReceiveLocations>
  <PrimaryReceiveLocation>string</PrimaryReceiveLocation>
\</Inline Model>
```