---
title: "Update Schema application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: fdb2e207-71b2-41ee-b064-30f543fbc48e
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Schema: application/json
## Update Schema (only tracking options and description)							
							
  Response Content Type: **application/json**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**schemaName** |(required)|Schema Name|path|{"Name": "string","TargetNameSpace": "string","RootName": "string","ApplicationName": "string","AssemblyName": "string","SchemaType": "string","Description": "string","Tracking": {"TrackedProperties": [{"PropertyName": "string","TrackingEnabled": true]}}|  							
**schema** |(required)||body|string|												
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
