---
title: "GET Specific Application application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 5944ba93-7976-4f8a-bee8-4a783f384fb6
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Specific Application: application/xml
## GET Specific Application

  Response Content Type: **application/xml**
  
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