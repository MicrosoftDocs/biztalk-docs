---
title: "Update Sendport text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: af3b1841-3cf7-4ea3-8bec-e3ac5b878cca
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Sendport: text/xml
## Update Sendport				
							
  Response Content Type: **text/xml**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**btSendPort** |(required)|Send port details|body||  							
**sendPortName** |(required)|Send port name|path|string|					

## Data Type		

```
\<?xml version="1.0"?>
<SendPort>
  <Name>string</Name>
  <Description>string</Description>
  <ApplicationName>string</ApplicationName>
  <IsDynamic>true</IsDynamic>
  <IsTwoWay>true</IsTwoWay>
  <Status>string</Status>
  <CustomData>string</CustomData>
  <PrimaryTransport>
    <Address>string</Address>
    <TransportType>string</TransportType>
    <TransportTypeData>string</TransportTypeData>
    <SendHandler>string</SendHandler>
    <RetryCount>1</RetryCount>
    <RetryInterval>1</RetryInterval>
    <OrderedDelivery>true</OrderedDelivery>
    <Schedule>
      <ServiceWindowEnabled>true</ServiceWindowEnabled>
      <FromTime>1970-01-01T00:00:00.001Z</FromTime>
      <ToTime>1970-01-01T00:00:00.001Z</ToTime>
    </Schedule>
  </PrimaryTransport>
  <SecondaryTransport>
    <Address>string</Address>
    <TransportType>string</TransportType>
    <TransportTypeData>string</TransportTypeData>
    <SendHandler>string</SendHandler>
    <RetryCount>1</RetryCount>
    <RetryInterval>1</RetryInterval>
    <OrderedDelivery>true</OrderedDelivery>
    <Schedule>
      <ServiceWindowEnabled>true</ServiceWindowEnabled>
      <FromTime>1970-01-01T00:00:00.001Z</FromTime>
      <ToTime>1970-01-01T00:00:00.001Z</ToTime>
    </Schedule>
  </SecondaryTransport>
  <SendPipeline>string</SendPipeline>
  <SendPipelineData>string</SendPipelineData>
  <ReceivePipeline>string</ReceivePipeline>
  <ReceivePipelineData>string</ReceivePipelineData>
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
  <EncryptionCert>
    <CommonName>string</CommonName>
    <Thumbprint>string</Thumbprint>
  </EncryptionCert>
  <Filter>string</Filter>
  <Priority>1</Priority>
  <RouteFailedMessage>true</RouteFailedMessage>
  <OrderedDelivery>true</OrderedDelivery>
  <StopSendingOnFailure>true</StopSendingOnFailure>
</SendPort>

```

						
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
