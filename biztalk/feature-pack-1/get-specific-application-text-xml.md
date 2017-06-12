---
title: "GET Specific Application text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 14fcb04a-a24f-4fb9-8819-63ed58af7060
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# GET Specific Application: text/xml
## GET Specific Application

  Response Content Type: **text/xml**
  
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