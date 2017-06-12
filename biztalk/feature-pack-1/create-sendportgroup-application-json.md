---
title: "Create SendPortGroup application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 761171e9-3ea9-459f-b129-b8ae56370e64
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create SendPortGroup: application/json
## Create SendPortGroup

  Response Content Type: **application/json**
  
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**sendPortGroup** |(required)||body|  { "Name": "string", "SendPorts": [ "string" ], "CustomData": "string", "Filter": "string", "Status": "string", "ApplicationName": "string", "Description": "string" }   |  							

## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
