---
title: "Update Transform application x www form  urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 71b7bbd7-2a37-4212-9932-6f71f5da4f6b
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Transform: application/x-www-form-  urlencoded
## Update Transform. Only Description can be edited							
							
  Response Content Type: **application/x-www-form-urlencoded**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**transformFullName** |(required)|Transform full name|path|string   |  							
**transform** |||body|{ "FullName": "string", "ApplicationName": "string", "Description": "string", "Assembly": "string", "SourceSchema": "string", "TargetSchema": "string", "XmlContent": "string" }|							
					
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
