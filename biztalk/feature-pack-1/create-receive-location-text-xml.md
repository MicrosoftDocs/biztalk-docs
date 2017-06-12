---
title: "Create Receive Location text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 86ce90c4-76b7-4241-b3e8-d5ef0418619e
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create Receive Location: text/xml
## Create Receive Location


Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|receiveLocation|(required)|Receive location details|body|Example Value|

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

Response Messages
---
|HTTP Status Code|Reason|Response Model|Headers|
|---|---|---|---|
|204|No Content|||
