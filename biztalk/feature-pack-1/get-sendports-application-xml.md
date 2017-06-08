---
title: "Get Sendports application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 296cca05-4a02-4dd4-a58f-3f26ec2f5dbb
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Sendports: application/xml
## Get Sendports

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  |http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/SendPorts |

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/SendPorts' |
| Response Code | 200|

## Response Body

```
\<ArrayOfSendPort xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <SendPort>
    <Name>ResponseSQL</Name>
    <ApplicationName>OldOrdersReceive</ApplicationName>
    <IsDynamic>false</IsDynamic>
    <IsTwoWay>false</IsTwoWay>
    <Status>Started</Status>
    <PrimaryTransport>
      <Address>C:\BizTalk\Orders\Response\%MessageID%.xml</Address>
      <TransportType>FILE</TransportType>
      <TransportTypeData>&lt;CustomProps&gt;&lt;FileName vt="8"&gt;%MessageID%.xml&lt;/FileName&gt;&lt;CopyMode vt="19"&gt;1&lt;/CopyMode&gt;&lt;AllowCacheOnWrite vt="11"&gt;0&lt;/AllowCacheOnWrite&gt;&lt;UseTempFileOnWrite vt="11"&gt;0&lt;/UseTempFileOnWrite&gt;&lt;/CustomProps&gt;</TransportTypeData>
      <SendHandler>SendHost</SendHandler>
      <RetryCount>3</RetryCount>
      <RetryInterval>5</RetryInterval>
      <OrderedDelivery>false</OrderedDelivery>
      <Schedule>
        <ServiceWindowEnabled>false</ServiceWindowEnabled>
        <FromTime>2000-01-01T00:00:00</FromTime>
        <ToTime>2000-01-01T23:59:59</ToTime>
      </Schedule>
    </PrimaryTransport>
    <SecondaryTransport>
      <Address />
      <RetryCount>3</RetryCount>
      <RetryInterval>5</RetryInterval>
      <OrderedDelivery>false</OrderedDelivery>
      <Schedule>
        <ServiceWindowEnabled>false</ServiceWindowEnabled>
        <FromTime>2000-01-01T00:00:00</FromTime>
        <ToTime>2000-01-01T23:59:59</ToTime>
      </Schedule>
    </SecondaryTransport>
    <SendPipeline>Microsoft.BizTalk.DefaultPipelines.PassThruTransmit</SendPipeline>
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
    <Filter />
    <Priority>5</Priority>
    <RouteFailedMessage>false</RouteFailedMessage>
    <OrderedDelivery>false</OrderedDelivery>
    <StopSendingOnFailure>false</StopSendingOnFailure>
  </SendPort>
  <SendPort>
    <Name>BackupFile</Name>
    <ApplicationName>OldOrdersReceive</ApplicationName>
    <IsDynamic>false</IsDynamic>
    <IsTwoWay>false</IsTwoWay>
    <Status>Started</Status>
    <PrimaryTransport>
      <Address>C:\BizTalk\Orders\Backup\%MessageID%.xml</Address>
      <TransportType>FILE</TransportType>
      <TransportTypeData>&lt;CustomProps&gt;&lt;FileName vt="8"&gt;%MessageID%.xml&lt;/FileName&gt;&lt;CopyMode vt="19"&gt;1&lt;/CopyMode&gt;&lt;AllowCacheOnWrite vt="11"&gt;0&lt;/AllowCacheOnWrite&gt;&lt;UseTempFileOnWrite vt="11"&gt;0&lt;/UseTempFileOnWrite&gt;&lt;/CustomProps&gt;</TransportTypeData>
      <SendHandler>SendHost</SendHandler>
      <RetryCount>3</RetryCount>
      <RetryInterval>5</RetryInterval>
      <OrderedDelivery>false</OrderedDelivery>
      <Schedule>
        <ServiceWindowEnabled>false</ServiceWindowEnabled>
        <FromTime>2000-01-01T00:00:00</FromTime>
        <ToTime>2000-01-01T23:59:59</ToTime>
      </Schedule>
    </PrimaryTransport>
    <SecondaryTransport>
      <Address />
      <RetryCount>3</RetryCount>
      <RetryInterval>5</RetryInterval>
      <OrderedDelivery>false</OrderedDelivery>
      <Schedule>
        <ServiceWindowEnabled>false</ServiceWindowEnabled>
        <FromTime>2000-01-01T00:00:00</FromTime>
        <ToTime>2000-01-01T23:59:59</ToTime>
      </Schedule>
    </SecondaryTransport>
    <SendPipeline>Microsoft.BizTalk.DefaultPipelines.PassThruTransmit</SendPipeline>
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
    <Filter />
    <Priority>5</Priority>
    <RouteFailedMessage>false</RouteFailedMessage>
    <OrderedDelivery>false</OrderedDelivery>
    <StopSendingOnFailure>false</StopSendingOnFailure>
  </SendPort>
  <SendPort>
    <Name>WcfSendPort_SqlAdapterBinding_TypedProcedures_dbo_Custom</Name>
    <Description>SendPort for SqlAdapterBinding.</Description>
    <ApplicationName>OldOrdersReceive</ApplicationName>
    <IsDynamic>false</IsDynamic>
    <IsTwoWay>true</IsTwoWay>
    <Status>Started</Status>
    <PrimaryTransport>
      <Address>mssql://biztalkfp1//MyCRM?</Address>
      <TransportType>WCF-Custom</TransportType>
      <TransportTypeData>
        &lt;CustomProps&gt;&lt;BindingConfiguration vt="8"&gt;&amp;lt;binding name="SqlAdapterBinding" maxConnectionPoolSize="100" encrypt="false" workstationId="" useAmbientTransaction="true" batchSize="20" ApplicationIntent="ReadWrite" MultiSubnetFailover="true" polledDataAvailableStatement="" pollingStatement="" pollingIntervalInSeconds="30" pollWhileDataFound="false" notificationStatement="" notifyOnListenerStart="true" enableBizTalkCompatibilityMode="true" chunkSize="4194304" inboundOperationType="Polling" useDatabaseNameInXsdNamespace="false" allowIdentityInsert="false" acceptCredentialsInUri="false" enablePerformanceCounters="false" xmlStoredProcedureRootNodeName="" xmlStoredProcedureRootNodeNamespace="" /&amp;gt;&lt;/BindingConfiguration&gt;&lt;InboundBodyPathExpression vt="8" /&gt;&lt;UseSSO vt="11"&gt;0&lt;/UseSSO&gt;&lt;BindingType vt="8"&gt;sqlBinding&lt;/BindingType&gt;&lt;OutboundXmlTemplate vt="8"&gt;&amp;lt;bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/&amp;gt;&lt;/OutboundXmlTemplate&gt;&lt;ProxyUserName vt="8" /&gt;&lt;UserName vt="8" /&gt;&lt;OutboundBodyLocation vt="8"&gt;UseBodyElement&lt;/OutboundBodyLocation&gt;&lt;IsolationLevel vt="8"&gt;Serializable&lt;/IsolationLevel&gt;&lt;EnableTransaction vt="11"&gt;-1&lt;/EnableTransaction&gt;&lt;StaticAction vt="8"&gt;&amp;lt;BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"&amp;gt;
          &amp;lt;Operation Name="Operation_1" Action="TypedProcedure/dbo/addOldOrders" /&amp;gt;
      &amp;lt;/BtsActionMapping&amp;gt;&lt;/StaticAction&gt;&lt;AffiliateApplicationName vt="8" /&gt;&lt;InboundNodeEncoding vt="8"&gt;Xml&lt;/InboundNodeEncoding&gt;&lt;PropagateFaultMessage vt="11"&gt;-1&lt;/PropagateFaultMessage&gt;&lt;ProxyAddress vt="8" /&gt;&lt;Identity vt="8" /&gt;&lt;InboundBodyLocation vt="8"&gt;UseBodyElement&lt;/InboundBodyLocation&gt;&lt;/CustomProps&gt;</TransportTypeData>
      <SendHandler>SendHost</SendHandler>
      <RetryCount>3</RetryCount>
      <RetryInterval>5</RetryInterval>
      <OrderedDelivery>false</OrderedDelivery>
      <Schedule>
        <ServiceWindowEnabled>false</ServiceWindowEnabled>
        <FromTime>2000-01-01T00:00:00</FromTime>
        <ToTime>2000-01-01T23:59:59</ToTime>
      </Schedule>
    </PrimaryTransport>
    <SecondaryTransport>
      <Address />
      <RetryCount>3</RetryCount>
      <RetryInterval>5</RetryInterval>
      <OrderedDelivery>false</OrderedDelivery>
      <Schedule>
        <ServiceWindowEnabled>false</ServiceWindowEnabled>
        <FromTime>2000-01-01T00:00:00</FromTime>
        <ToTime>2000-01-01T23:59:59</ToTime>
      </Schedule>
    </SecondaryTransport>
    <SendPipeline>Microsoft.BizTalk.DefaultPipelines.XMLTransmit</SendPipeline>
    <ReceivePipeline>Microsoft.BizTalk.DefaultPipelines.XMLReceive</ReceivePipeline>
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
    <Filter />
    <Priority>5</Priority>
    <RouteFailedMessage>false</RouteFailedMessage>
    <OrderedDelivery>false</OrderedDelivery>
    <StopSendingOnFailure>false</StopSendingOnFailure>
  </SendPort>
</ArrayOfSendPort>
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 04:02:17 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "7703",
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
\</Inline Model>

```
