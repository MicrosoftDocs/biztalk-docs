---
title: "Update Schema text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 820c6ad3-82bc-425b-9156-2a28a44e9321
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Schema: text/json
## Update Schema (only tracking options and description)							
							
  Response Content Type: **text/json**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**schemaName** |(required)|Schema Name|path|{"Name": "string","TargetNameSpace": "string","RootName": "string","ApplicationName": "string","AssemblyName": "string","SchemaType": "string","Description": "string","Tracking": {"TrackedProperties": [{"PropertyName": "string","TrackingEnabled": true]}}|  							
**schema** |(required)||body|string|												
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
