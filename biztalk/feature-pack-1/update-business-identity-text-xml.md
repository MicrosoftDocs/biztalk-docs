---
title: "Update business identity text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 4eaedf6d-b15a-4a12-b8cf-189b0c95b7ed
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update business identity: text/xml
## Create business identity

  Response Content Type: **text/xml**

Parameters
---


Parameter|Value  |Description |Parameter Type|Data Type  
---------|---------|---------|---------|---------
qualifierIdentity|(required)|Qualifier identity details|body|    |
partyName|(required)|Party name|path|string|
profileName|(required)|Business profile Name|path|string|
|id|(required)|Business profile id|path|integer|
Response Messages
---



HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204     |No Content |         |       |

  
Example Value
---

```
\<?xml version="1.0"?>
<QualifierIdentity>
  <Description>string</Description>
  <Qualifier>string</Qualifier>
  <Value>string</Value>
  <Id>1</Id>
</QualifierIdentity>
```
