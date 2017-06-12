---
title: "Update Schema application x www form  urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 1ecae830-45fb-4111-8382-6cac03d326ce
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Schema: application/x-www-form-  urlencoded
## Update Schema (only tracking options and description)							
							
  Response Content Type: **application/x-www-form-urlencoded**							
							
## *Parameters*							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**schemaName** |(required)|Schema Name|path| { "Name": "string", "TargetNameSpace": "string", "RootName": "string", "ApplicationName": "string", "AssemblyName": "string", "SchemaType": "string", "Description": "string", "Tracking": { "TrackedProperties": [ { "PropertyName": "string", "TrackingEnabled": true } ] } } |  							
**schema** |(required)||body|string|		

schemaName Data Type


										
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
