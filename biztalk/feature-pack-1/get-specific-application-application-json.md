---
title: "GET Specific Application application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: e054e7cb-3154-4b60-b603-732d8aec4e52
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Specific Application: application/json
## GET Specific Application

  Response Content Type: **application/json**
  
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