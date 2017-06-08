---
title: "Get Sendports text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 99281667-31f5-47e0-b0c7-f99ce1f740f8
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Sendports: text/json
## Get Sendports

  Response Content Type: **text/json**

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
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/SendPorts' |
| Response Code | 200|

## Response Body

```
[{"Name":"ResponseSQL","Description":null,"ApplicationName":"OldOrdersReceive","IsDynamic":false,"IsTwoWay":false,"Status":"Started","CustomData":null,"PrimaryTransport":{"Address":"C:\\BizTalk\\Orders\\Response\\%MessageID%.xml","TransportType":"FILE","TransportTypeData":"<CustomProps><FileName vt=\"8\">%MessageID%.xml</FileName><CopyMode vt=\"19\">1</CopyMode><AllowCacheOnWrite vt=\"11\">0</AllowCacheOnWrite><UseTempFileOnWrite vt=\"11\">0</UseTempFileOnWrite></CustomProps>","SendHandler":"SendHost","RetryCount":3,"RetryInterval":5,"OrderedDelivery":false,"Schedule":{"ServiceWindowEnabled":false,"FromTime":"2000-01-01T00:00:00","ToTime":"2000-01-01T23:59:59"}},"SecondaryTransport":{"Address":"","TransportType":null,"TransportTypeData":null,"SendHandler":null,"RetryCount":3,"RetryInterval":5,"OrderedDelivery":false,"Schedule":{"ServiceWindowEnabled":false,"FromTime":"2000-01-01T00:00:00","ToTime":"2000-01-01T23:59:59"}},"SendPipeline":"Microsoft.BizTalk.DefaultPipelines.PassThruTransmit","SendPipelineData":null,"ReceivePipeline":null,"ReceivePipelineData":null,"InboundTransforms":[],"OutboundTransforms":[],"Tracking":{"Body":{"BeforeSendPipeline":false,"AfterSendPipeline":false,"BeforeReceivePipeline":false,"AfterReceivePipeline":false},"Property":{"BeforeSendPipeline":false,"AfterSendPipeline":false,"BeforeReceivePipeline":false,"AfterReceivePipeline":false}},"EncryptionCert":null,"Filter":"","Priority":5,"RouteFailedMessage":false,"OrderedDelivery":false,"StopSendingOnFailure":false},{"Name":"BackupFile","Description":null,"ApplicationName":"OldOrdersReceive","IsDynamic":false,"IsTwoWay":false,"Status":"Started","CustomData":null,"PrimaryTransport":{"Address":"C:\\BizTalk\\Orders\\Backup\\%MessageID%.xml","TransportType":"FILE","TransportTypeData":"<CustomProps><FileName vt=\"8\">%MessageID%.xml</FileName><CopyMode vt=\"19\">1</CopyMode><AllowCacheOnWrite vt=\"11\">0</AllowCacheOnWrite><UseTempFileOnWrite vt=\"11\">0</UseTempFileOnWrite></CustomProps>","SendHandler":"SendHost","RetryCount":3,"RetryInterval":5,"OrderedDelivery":false,"Schedule":{"ServiceWindowEnabled":false,"FromTime":"2000-01-01T00:00:00","ToTime":"2000-01-01T23:59:59"}},"SecondaryTransport":{"Address":"","TransportType":null,"TransportTypeData":null,"SendHandler":null,"RetryCount":3,"RetryInterval":5,"OrderedDelivery":false,"Schedule":{"ServiceWindowEnabled":false,"FromTime":"2000-01-01T00:00:00","ToTime":"2000-01-01T23:59:59"}},"SendPipeline":"Microsoft.BizTalk.DefaultPipelines.PassThruTransmit","SendPipelineData":null,"ReceivePipeline":null,"ReceivePipelineData":null,"InboundTransforms":[],"OutboundTransforms":[],"Tracking":{"Body":{"BeforeSendPipeline":false,"AfterSendPipeline":false,"BeforeReceivePipeline":false,"AfterReceivePipeline":false},"Property":{"BeforeSendPipeline":false,"AfterSendPipeline":false,"BeforeReceivePipeline":false,"AfterReceivePipeline":false}},"EncryptionCert":null,"Filter":"","Priority":5,"RouteFailedMessage":false,"OrderedDelivery":false,"StopSendingOnFailure":false},{"Name":"WcfSendPort_SqlAdapterBinding_TypedProcedures_dbo_Custom","Description":"SendPort for SqlAdapterBinding.","ApplicationName":"OldOrdersReceive","IsDynamic":false,"IsTwoWay":true,"Status":"Started","CustomData":null,"PrimaryTransport":{"Address":"mssql://biztalkfp1//MyCRM?","TransportType":"WCF-Custom","TransportTypeData":"<CustomProps><BindingConfiguration vt=\"8\">&lt;binding name=\"SqlAdapterBinding\" maxConnectionPoolSize=\"100\" encrypt=\"false\" workstationId=\"\" useAmbientTransaction=\"true\" batchSize=\"20\" ApplicationIntent=\"ReadWrite\" MultiSubnetFailover=\"true\" polledDataAvailableStatement=\"\" pollingStatement=\"\" pollingIntervalInSeconds=\"30\" pollWhileDataFound=\"false\" notificationStatement=\"\" notifyOnListenerStart=\"true\" enableBizTalkCompatibilityMode=\"true\" chunkSize=\"4194304\" inboundOperationType=\"Polling\" useDatabaseNameInXsdNamespace=\"false\" allowIdentityInsert=\"false\" acceptCredentialsInUri=\"false\" enablePerformanceCounters=\"false\" xmlStoredProcedureRootNodeName=\"\" xmlStoredProcedureRootNodeNamespace=\"\" /&gt;</BindingConfiguration><InboundBodyPathExpression vt=\"8\" /><UseSSO vt=\"11\">0</UseSSO><BindingType vt=\"8\">sqlBinding</BindingType><OutboundXmlTemplate vt=\"8\">&lt;bts-msg-body xmlns=\"http://www.microsoft.com/schemas/bts2007\" encoding=\"xml\"/&gt;</OutboundXmlTemplate><ProxyUserName vt=\"8\" /><UserName vt=\"8\" /><OutboundBodyLocation vt=\"8\">UseBodyElement</OutboundBodyLocation><IsolationLevel vt=\"8\">Serializable</IsolationLevel><EnableTransaction vt=\"11\">-1</EnableTransaction><StaticAction vt=\"8\">&lt;BtsActionMapping xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\" xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\"&gt;\r\n  &lt;Operation Name=\"Operation_1\" Action=\"TypedProcedure/dbo/addOldOrders\" /&gt;\r\n&lt;/BtsActionMapping&gt;</StaticAction><AffiliateApplicationName vt=\"8\" /><InboundNodeEncoding vt=\"8\">Xml</InboundNodeEncoding><PropagateFaultMessage vt=\"11\">-1</PropagateFaultMessage><ProxyAddress vt=\"8\" /><Identity vt=\"8\" /><InboundBodyLocation vt=\"8\">UseBodyElement</InboundBodyLocation></CustomProps>","SendHandler":"SendHost","RetryCount":3,"RetryInterval":5,"OrderedDelivery":false,"Schedule":{"ServiceWindowEnabled":false,"FromTime":"2000-01-01T00:00:00","ToTime":"2000-01-01T23:59:59"}},"SecondaryTransport":{"Address":"","TransportType":null,"TransportTypeData":null,"SendHandler":null,"RetryCount":3,"RetryInterval":5,"OrderedDelivery":false,"Schedule":{"ServiceWindowEnabled":false,"FromTime":"2000-01-01T00:00:00","ToTime":"2000-01-01T23:59:59"}},"SendPipeline":"Microsoft.BizTalk.DefaultPipelines.XMLTransmit","SendPipelineData":null,"ReceivePipeline":"Microsoft.BizTalk.DefaultPipelines.XMLReceive","ReceivePipelineData":null,"InboundTransforms":[],"OutboundTransforms":[],"Tracking":{"Body":{"BeforeSendPipeline":false,"AfterSendPipeline":false,"BeforeReceivePipeline":false,"AfterReceivePipeline":false},"Property":{"BeforeSendPipeline":false,"AfterSendPipeline":false,"BeforeReceivePipeline":false,"AfterReceivePipeline":false}},"EncryptionCert":null,"Filter":"","Priority":5,"RouteFailedMessage":false,"OrderedDelivery":false,"StopSendingOnFailure":false}]

```



Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 03:58:16 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "6228",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "Description": "string",
    "ApplicationName": "string",
    "IsDynamic": true,
    "IsTwoWay": true,
    "Status": "string",
    "CustomData": "string",
    "PrimaryTransport": {
      "Address": "string",
      "TransportType": "string",
      "TransportTypeData": "string",
      "SendHandler": "string",
      "RetryCount": 0,
      "RetryInterval": 0,
      "OrderedDelivery": true,
      "Schedule": {
        "ServiceWindowEnabled": true,
        "FromTime": "2017-04-23T12:05:45.972Z",
        "ToTime": "2017-04-23T12:05:45.972Z"
      }
    },
    "SecondaryTransport": {
      "Address": "string",
      "TransportType": "string",
      "TransportTypeData": "string",
      "SendHandler": "string",
      "RetryCount": 0,
      "RetryInterval": 0,
      "OrderedDelivery": true,
      "Schedule": {
        "ServiceWindowEnabled": true,
        "FromTime": "2017-04-23T12:05:45.972Z",
        "ToTime": "2017-04-23T12:05:45.972Z"
      }
    },
    "SendPipeline": "string",
    "SendPipelineData": "string",
    "ReceivePipeline": "string",
    "ReceivePipelineData": "string",
    "InboundTransforms": [
      "string"
    ],
    "OutboundTransforms": [
      "string"
    ],
    "Tracking": {
      "Body": {
        "BeforeSendPipeline": true,
        "AfterSendPipeline": true,
        "BeforeReceivePipeline": true,
        "AfterReceivePipeline": true
      },
      "Property": {
        "BeforeSendPipeline": true,
        "AfterSendPipeline": true,
        "BeforeReceivePipeline": true,
        "AfterReceivePipeline": true
      }
    },
    "EncryptionCert": {
      "CommonName": "string",
      "Thumbprint": "string"
    },
    "Filter": "string",
    "Priority": 0,
    "RouteFailedMessage": true,
    "OrderedDelivery": true,
    "StopSendingOnFailure": true
  }
]

```
