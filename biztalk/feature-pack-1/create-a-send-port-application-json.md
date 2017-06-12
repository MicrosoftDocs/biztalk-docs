---
title: "Create a send port application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: e2a87796-e9a0-413c-85e8-4d29fd742105
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create a send port: application/json
## Create a send port		
							
  Response Content Type: **application/json**							
							
## Parameters							
							
							
							
Parameter|Value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**btSendPort** |(required)|Send port details|body|{ "Name": "string", "Description": "string", "ApplicationName": "string", "IsDynamic": true, "IsTwoWay": true, "Status": "string", "CustomData": "string", "PrimaryTransport": { "Address": "string", "TransportType": "string", "TransportTypeData": "string", "SendHandler": "string", "RetryCount": 0, "RetryInterval": 0, "OrderedDelivery": true, "Schedule": { "ServiceWindowEnabled": true, "FromTime": "2017-04-23T12:05:45.991Z", "ToTime": "2017-04-23T12:05:45.991Z" } }, "SecondaryTransport": { "Address": "string", "TransportType": "string", "TransportTypeData": "string", "SendHandler": "string", "RetryCount": 0, "RetryInterval": 0, "OrderedDelivery": true, "Schedule": { "ServiceWindowEnabled": true, "FromTime": "2017-04-23T12:05:45.991Z", "ToTime": "2017-04-23T12:05:45.991Z" } }, "SendPipeline": "string", "SendPipelineData": "string", "ReceivePipeline": "string", "ReceivePipelineData": "string", "InboundTransforms": [ "string" ], "OutboundTransforms": [ "string" ], "Tracking": { "Body": { "BeforeSendPipeline": true, "AfterSendPipeline": true, "BeforeReceivePipeline": true, "AfterReceivePipeline": true }, "Property": { "BeforeSendPipeline": true, "AfterSendPipeline": true, "BeforeReceivePipeline": true, "AfterReceivePipeline": true } }, "EncryptionCert": { "CommonName": "string", "Thumbprint": "string" }, "Filter": "string", "Priority": 0, "RouteFailedMessage": true, "OrderedDelivery": true, "StopSendingOnFailure": true }     |  							
						
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
