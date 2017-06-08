---
title: "Update Sendport application x www form urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 1010717b-8374-4fd7-8b39-e423d8288eec
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Sendport: application/x-www-form-urlencoded
## Update Sendport				
							
  Response Content Type: **application/x-www-form-urlencoded**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**btSendPort** |(required)|Send port details|body|{ "Name": "string", "Description": "string", "ApplicationName": "string", "IsDynamic": true, "IsTwoWay": true, "Status": "string", "CustomData": "string", "PrimaryTransport": { "Address": "string", "TransportType": "string", "TransportTypeData": "string", "SendHandler": "string", "RetryCount": 0, "RetryInterval": 0, "OrderedDelivery": true, "Schedule": { "ServiceWindowEnabled": true, "FromTime": "2017-04-23T12:05:46.036Z", "ToTime": "2017-04-23T12:05:46.036Z" } }, "SecondaryTransport": { "Address": "string", "TransportType": "string", "TransportTypeData": "string", "SendHandler": "string", "RetryCount": 0, "RetryInterval": 0, "OrderedDelivery": true, "Schedule": { "ServiceWindowEnabled": true, "FromTime": "2017-04-23T12:05:46.036Z", "ToTime": "2017-04-23T12:05:46.036Z" } }, "SendPipeline": "string", "SendPipelineData": "string", "ReceivePipeline": "string", "ReceivePipelineData": "string", "InboundTransforms": [ "string" ], "OutboundTransforms": [ "string" ], "Tracking": { "Body": { "BeforeSendPipeline": true, "AfterSendPipeline": true, "BeforeReceivePipeline": true, "AfterReceivePipeline": true }, "Property": { "BeforeSendPipeline": true, "AfterSendPipeline": true, "BeforeReceivePipeline": true, "AfterReceivePipeline": true } }, "EncryptionCert": { "CommonName": "string", "Thumbprint": "string" }, "Filter": "string", "Priority": 0, "RouteFailedMessage": true, "OrderedDelivery": true, "StopSendingOnFailure": true } |  							
**sendPortName** |(required)|Send port name|path|string|							
						
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
