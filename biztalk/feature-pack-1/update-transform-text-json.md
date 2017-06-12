---
title: "Update Transform text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 5924cc97-61a1-4fda-8f14-2f7b29a6c081
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Transform: text/json
## Update Transform. Only Description can be edited							
							
  Response Content Type: **text/json**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**transformFullName** |(required)|Transform full name|path|string   |  							
**transform** |||body|{ "FullName": "string", "ApplicationName": "string", "Description": "string", "Assembly": "string", "SourceSchema": "string", "TargetSchema": "string", "XmlContent": "string" }|							
					
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
