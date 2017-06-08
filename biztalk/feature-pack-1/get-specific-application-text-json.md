---
title: "GET Specific Application text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 677b8d6d-9b64-417c-ba93-baec808b129e
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Specific Application: text/json
## GET Specific Application

  Response Content Type: **text/json**
  
Response Class (Status 200)
---

OK



Parameters
---



Parameter  |Value  |Description  |Parameter Type |Data Type 
---------|---------|---------|---------|---------
applicationName |(required) |Application Name |path      |string   | 



Example Value
---

```
{
  "Name": "string",
  "Description": "string",
  "IsDefaultApplication": true,
  "IsSystem": true,
  "Status": "string",
  "IsConfigured": true,
  "ApplicationReferences": [
    "string"
  ],
  "ApplicationBackReferences": [
    "string"
  ]
}
```