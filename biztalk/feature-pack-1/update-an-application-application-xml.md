---
title: "Update an Application application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 46a0cc30-f3df-4633-927a-0e24629cd5fc
caps.latest.revision: 4
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update an Application: application/xml
## Update an Application

  Response Content Type: **application/xml**
  
  Parameters
  ---
  
  

Parameter |Value |Description |Parameter Type|Data Type
---------|---------|---------|---------|---------
applicationName|(required)   |Name of Application to be updated|path |string |
application|(required)    |Details of Application to be updated|body  |   |


Response Messages
---

HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204   |No Content    |         |         |

Example Value
---

```
\<?xml version="1.0"?>
<Application>
  <Name>string</Name>
  <Description>string</Description>
  <IsDefaultApplication>true</IsDefaultApplication>
  <IsSystem>true</IsSystem>
  <Status>string</Status>
  <IsConfigured>true</IsConfigured>
  <ApplicationReferences>string</ApplicationReferences>
  <ApplicationBackReferences>string</ApplicationBackReferences>
</Application>
```

