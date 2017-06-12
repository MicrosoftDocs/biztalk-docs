---
title: "Get a schemas by name text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: cb6ae9aa-ad64-46b3-923d-c3e22bfa3dbb
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get a schemas by name: text/json
## GET a schemas by name.

  Response Content Type: **text/json**

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
