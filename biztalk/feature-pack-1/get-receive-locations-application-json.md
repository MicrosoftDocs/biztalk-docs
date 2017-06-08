---
title: "Get Receive Locations application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 9315e6de-569b-43a2-87da-cb03c299d9f9
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Receive Locations: application/json
## Get Receive Locations

  Response Content Type: **application/json**

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
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations'|
| Response Code | 200|

Response Body
---
```
[
  {
    "Name": "OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0_ReceiveLocation",
    "Description": null,
    "ReceivePortName": "OldOrdersReceive_1.0.0.0_AddDataToSQL.ProcessOrders_ReceiveOrderFromFile_2aa35c52bb10d3e0",
    "Enable": true,
    "IsPrimary": true,
    "Address": "C:\\BizTalk\\Orders\\Input\\Order_*.xml",
    "PublicAddress": "",
    "TransportType": "FILE",
    "TransportTypeData": "<CustomProps>\<FileMask vt=\"8\">Order_*.xml</FileMask>\<RemoveReceivedFileDelay vt=\"19\">10</RemoveReceivedFileDelay>\<RemoveReceivedFileRetryCount vt=\"19\">5</RemoveReceivedFileRetryCount>\<RemoveReceivedFileMaxInterval vt=\"19\">300000</RemoveReceivedFileMaxInterval>\<FileNetFailRetryCount vt=\"19\">5</FileNetFailRetryCount>\<PollingInterval vt=\"19\">60000</PollingInterval>\<BatchSize vt=\"19\">20</BatchSize>\<FileNetFailRetryInt vt=\"19\">5</FileNetFailRetryInt>\<RenameReceivedFiles vt=\"11\">0</RenameReceivedFiles>\<BatchSizeInBytes vt=\"19\">102400</BatchSizeInBytes></CustomProps>",
    "ReceiveHandler": "ReceiveHost",
    "CustomData": null,
    "ReceivePipeline": "AddDataToSQL.ReceivePipeline1",
    "ReceivePipelineData": null,
    "SendPipeline": null,
    "SendPipelineData": null,
    "Schedule": {
      "StartDate": "2000-01-01T00:00:00",
      "StartDateEnabled": false,
      "EndDate": "2017-03-31T23:59:59",
      "EndDateEnabled": false,
      "ServiceWindowEnabled": false,
      "FromTime": "2000-01-01T00:00:00",
      "ToTime": "2000-01-01T23:59:59"
    },
    "EncryptionCert": null,
    "FragmentMessages": "Runtime"
  }
]
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 04:51:13 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "1422",
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
    "ReceivePortName": "string",
    "Enable": true,
    "IsPrimary": true,
    "Address": "string",
    "PublicAddress": "string",
    "TransportType": "string",
    "TransportTypeData": "string",
    "ReceiveHandler": "string",
    "CustomData": "string",
    "ReceivePipeline": "string",
    "ReceivePipelineData": "string",
    "SendPipeline": "string",
    "SendPipelineData": "string",
    "Schedule": {
      "StartDate": "2017-04-21T00:37:36.230Z",
      "StartDateEnabled": true,
      "EndDate": "2017-04-21T00:37:36.230Z",
      "EndDateEnabled": true,
      "ServiceWindowEnabled": true,
      "FromTime": "2017-04-21T00:37:36.230Z",
      "ToTime": "2017-04-21T00:37:36.230Z"
    },
    "EncryptionCert": {
      "CommonName": "string",
      "Thumbprint": "string"
    },
    "FragmentMessages": "string"
  }
]
```