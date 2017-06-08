---
title: "Add an enlisted party application x www form urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 6113e370-2f21-4653-8498-6b3222e06942
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Add an enlisted party: application/x-www-form-urlencoded
## Add an enlisted party

  Response Content Type: **application/x-xxx-form-urlencoded**

## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**enlistedParties** |(required)|list of Enlisted party details|body|  [{"Name": "string","Mappings": [{"PortTypeName": "string","OperationName": "string","SendPort": "string"}]}]  |  							
**applicationName** |(required)|Application name|path|string|							
**roleLinkName**    |(required)|Role link name|path|string|					


		
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
