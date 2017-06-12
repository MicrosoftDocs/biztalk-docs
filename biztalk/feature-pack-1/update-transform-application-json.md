---
title: "Update Transform application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: d0ea9a4b-a28b-419b-83c1-a85c2e328baa
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Transform: application/json
## Update Transform. Only Description can be edited							
							
  Response Content Type: **application/json**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**transformFullName** |(required)|Transform full name|path|string   |  							
**transform** |||body|{ "FullName": "string", "ApplicationName": "string", "Description": "string", "Assembly": "string", "SourceSchema": "string", "TargetSchema": "string", "XmlContent": "string" }|							
					
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
