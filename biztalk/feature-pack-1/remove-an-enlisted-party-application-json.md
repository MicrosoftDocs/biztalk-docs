---
title: "remove an enlisted party application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 76cd31dd-5404-4f95-957b-d8dc4016168f
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# remove an enlisted party: application/json
## remove an enlisted party	
							
  Response Content Type: **application/json**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**enlistedParties** |(required)|List of party names|body|	Array[string] |  							
**applicationName** |(required)|Application name|path|string|							
**roleLinkName**    |(required)|Role link name|path|string|							
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
