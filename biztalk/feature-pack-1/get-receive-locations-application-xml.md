---
title: "Get Receive Locations application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 9c54514c-2a1d-4954-b59f-7676ba882ecd
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Receive Locations: application/xml
## Get Receive Locations

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations'|
| Response Code | 200|

Response Body
---
```\<ArrayOfReceiveLocation xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <ReceiveLocation>
    <Name>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation</Name>
    <ReceivePortName>OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0</ReceivePortName>
    <Enable>true</Enable>
    <IsPrimary>true</IsPrimary>
    <Address>C:\BizTalk\Orders\Input\Order_*.xml</Address>
    <PublicAddress />
    <TransportType>FILE</TransportType>
    <TransportTypeData>&lt;CustomProps&gt;&lt;FileMask vt="8"&gt;Order_*.xml&lt;/FileMask&gt;&lt;RemoveReceivedFileDelay vt="19"&gt;10&lt;/RemoveReceivedFileDelay&gt;&lt;RemoveReceivedFileRetryCount vt="19"&gt;5&lt;/RemoveReceivedFileRetryCount&gt;&lt;RemoveReceivedFileMaxInterval vt="19"&gt;300000&lt;/RemoveReceivedFileMaxInterval&gt;&lt;FileNetFailRetryCount vt="19"&gt;5&lt;/FileNetFailRetryCount&gt;&lt;PollingInterval vt="19"&gt;60000&lt;/PollingInterval&gt;&lt;BatchSize vt="19"&gt;20&lt;/BatchSize&gt;&lt;FileNetFailRetryInt vt="19"&gt;5&lt;/FileNetFailRetryInt&gt;&lt;RenameReceivedFiles vt="11"&gt;0&lt;/RenameReceivedFiles&gt;&lt;BatchSizeInBytes vt="19"&gt;102400&lt;/BatchSizeInBytes&gt;&lt;/CustomProps&gt;</TransportTypeData>
    <ReceiveHandler>ReceiveHost</ReceiveHandler>
    <ReceivePipeline>AddDataToSQL.ReceivePipeline1</ReceivePipeline>
    <Schedule>
      <StartDate>2000-01-01T00:00:00</StartDate>
      <StartDateEnabled>false</StartDateEnabled>
      <EndDate>2017-03-31T23:59:59</EndDate>
      <EndDateEnabled>false</EndDateEnabled>
      <ServiceWindowEnabled>false</ServiceWindowEnabled>
      <FromTime>2000-01-01T00:00:00</FromTime>
      <ToTime>2000-01-01T23:59:59</ToTime>
    </Schedule>
    <FragmentMessages>Runtime</FragmentMessages>
  </ReceiveLocation>
</ArrayOfReceiveLocation>
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 05:15:48 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1775",
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
\</Inline Model>
```