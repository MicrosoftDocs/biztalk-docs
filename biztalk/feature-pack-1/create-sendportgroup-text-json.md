---
title: "Create SendPortGroup text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f5e2fcd5-af69-4245-a6e6-1c1bfdf717e1
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create SendPortGroup: text/json
## Create SendPortGroup

  Response Content Type: **text/json**

## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**sendPortGroup** |(required)||body|  { "Name": "string", "SendPorts": [ "string" ], "CustomData": "string", "Filter": "string", "Status": "string", "ApplicationName": "string", "Description": "string" }   |  							

## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
