---
title: "Get Receive Ports application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f9a90ed8-d340-4898-bf2c-39e4c90c0691
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Receive Ports: application/xml
## Get Receive Ports

  Response Content Type: **application/xml**

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
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceivePorts'|
| Response Code | 200|

Response Body
---
```
\<ArrayOfReceivePort xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <ReceivePort>
    <Name>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0</Name>
    <IsTwoWay>false</IsTwoWay>
    <ApplicationName>OldOrdersReceive</ApplicationName>
    <InboundTransforms />
    <OutboundTransforms />
    <Tracking>
      <Body>
        <BeforeSendPipeline>false</BeforeSendPipeline>
        <AfterSendPipeline>false</AfterSendPipeline>
        <BeforeReceivePipeline>false</BeforeReceivePipeline>
        <AfterReceivePipeline>false</AfterReceivePipeline>
      </Body>
      <Property>
        <BeforeSendPipeline>false</BeforeSendPipeline>
        <AfterSendPipeline>false</AfterSendPipeline>
        <BeforeReceivePipeline>false</BeforeReceivePipeline>
        <AfterReceivePipeline>false</AfterReceivePipeline>
      </Property>
    </Tracking>
    <ReceiveLocations>
      <string>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation</string>
    </ReceiveLocations>
    <PrimaryReceiveLocation>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation</PrimaryReceiveLocation>
  </ReceivePort>
</ArrayOfReceivePort>
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 07:01:34 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
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