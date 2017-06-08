---
title: "Get a schemas by name application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 059c06ef-ea1d-4b0f-8d25-dc44343c91b4
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get a schemas by name: application/json
## GET a schemas by name.

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK


## Parameters	
Parameter  |Value  |Description  |Parameter Type  |Data Type  	
---------|---------|---------|---------|---------| 	
schemaName|  (required)       | Name of the schema.|path  |  string | 	

## Example Value

```
{
  "Name": "string",
  "TargetNameSpace": "string",
  "RootName": "string",
  "ApplicationName": "string",
  "AssemblyName": "string",
  "SchemaType": "string",
  "Description": "string",
  "Tracking": {
    "TrackedProperties": [
      {
        "PropertyName": "string",
        "TrackingEnabled": true
      }
    ]
  }
}
```
