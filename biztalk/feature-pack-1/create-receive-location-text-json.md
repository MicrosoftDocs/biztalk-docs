---
title: "Create Receive Location text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 777cb455-e407-40cd-a36e-cdf1b50e1fda
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create Receive Location: text/json
## Create Receive Location


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
    "StartDate": "2017-04-24T01:48:22.322Z",
    "StartDateEnabled": true,
    "EndDate": "2017-04-24T01:48:22.322Z",
    "EndDateEnabled": true,
    "ServiceWindowEnabled": true,
    "FromTime": "2017-04-24T01:48:22.322Z",
    "ToTime": "2017-04-24T01:48:22.322Z"
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
