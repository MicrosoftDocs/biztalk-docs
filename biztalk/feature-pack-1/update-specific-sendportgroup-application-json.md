---
title: "Update specific SendPortGroup application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 0f02caff-9a1a-40f9-9c8a-2bb7dba8ff81
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update specific SendPortGroup: application/json
## Update specific SendPortGroup	
							
  Response Content Type: **application/json**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**sendPortGroup** |(required)|Details of SendPortGroup|body|{ "Name": "string", "SendPorts": [ "string" ], "CustomData": "string", "Filter": "string", "Status": "string", "ApplicationName": "string", "Description": "string" }|  							
**sendPortGroupName** |(required)|SendPortGroup Name|path|string|							
						
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
