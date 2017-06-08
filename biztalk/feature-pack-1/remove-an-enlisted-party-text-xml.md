---
title: "remove an enlisted party text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 82375d56-6d6a-4d91-8238-fb88bbe7edd8
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# remove an enlisted party: text/xml
## remove an enlisted party	
							
  Response Content Type: **text/xml**							
							
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
