---
title: "Update Receive Location text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 9e319cfa-3f00-4f65-903c-c6e20f342100
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Receive Location: text/json
## Update Receive Location


Parameters
---
|Parameter|Value|Description|Parameter Type|Data Type|
|---|---|---|---|---|
|receiveLocation|(required)|Receive location details|body|Example Value|

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
    "StartDate": "2017-04-24T01:48:22.355Z",
    "StartDateEnabled": true,
    "EndDate": "2017-04-24T01:48:22.355Z",
    "EndDateEnabled": true,
    "ServiceWindowEnabled": true,
    "FromTime": "2017-04-24T01:48:22.355Z",
    "ToTime": "2017-04-24T01:48:22.355Z"
  },
  "EncryptionCert": {
    "CommonName": "string",
    "Thumbprint": "string"
  },
  "FragmentMessages": "string"
}
```

Response Messages
---
|HTTP Status Code|Reason|Response Model|Headers|
|---|---|---|---|
|204|No Content|||
