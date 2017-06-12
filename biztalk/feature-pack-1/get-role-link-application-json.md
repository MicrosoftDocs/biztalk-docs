---
title: "Get Role link application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c5a2e87f-f99e-4ea0-9f7c-ea71920c8a3b
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Role link: application/json
## Get Role link

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK


Example Value
---

```
{
  "Name": "string",
  "ServiceLinkType": "string",
  "ApplicationName": "string",
  "AssemblyName": "string",
  "EnlistedParties": [
    {
      "Name": "string",
      "Mappings": [
        {
          "PortTypeName": "string",
          "OperationName": "string",
          "SendPort": "string"
        }
      ]
    }
  ]
}

```

## Parameter


Parameter  |Value  |Description  |Parameter Type  |Data Type  
---------|---------|---------|---------|---------| 
applicationName|  (required)       |         |       path  |  string | 
roleLinkName|      (required)   |         |       path  |     string | 

