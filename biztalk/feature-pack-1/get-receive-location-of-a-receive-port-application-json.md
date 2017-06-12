---
title: "Get receive location of a receive port application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 74fd9bc0-3e89-415b-becd-86434053cc3d
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get receive location of a receive port: application/json
## Get receive location of a receive port

  Response Content Type: **application/json**

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
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/ReceiveLocations/%7BreceivePortName%7D/%7BreceiveLocationName%7D'|
| Response Body | `{  "Message": "ReceivePort with name {receivePortName} does not exist." }`|
| Response Code | 404|

Response Headers
---
```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 07:45:21 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "69",
  "expires": "-1"
}
```

Example Value
---

```
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
    "StartDate": "2017-04-21T05:43:34.866Z",
    "StartDateEnabled": true,
    "EndDate": "2017-04-21T05:43:34.866Z",
    "EndDateEnabled": true,
    "ServiceWindowEnabled": true,
    "FromTime": "2017-04-21T05:43:34.866Z",
    "ToTime": "2017-04-21T05:43:34.866Z"
  },
  "EncryptionCert": {
    "CommonName": "string",
    "Thumbprint": "string"
  },
  "FragmentMessages": "string"
}
```
