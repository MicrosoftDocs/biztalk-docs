---
title: "Update specific SendPortGroup application x www form  urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 30d53301-3117-452b-82b1-7b1499fb42a4
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update specific SendPortGroup: application/x-www-form-  urlencoded
## Update specific SendPortGroup	
							
  Response Content Type: **application/x-www-form-urlencoded**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**sendPortGroup** |(required)|Details of SendPortGroup|body|{ "Name": "string", "SendPorts": [ "string" ], "CustomData": "string", "Filter": "string", "Status": "string", "ApplicationName": "string", "Description": "string" }|  							
**sendPortGroupName** |(required)|SendPortGroup Name|path|string|							
						
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
