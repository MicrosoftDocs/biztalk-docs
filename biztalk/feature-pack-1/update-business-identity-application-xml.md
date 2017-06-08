---
title: "Update business identity application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 2a1025ad-2746-4492-b443-225f5812642b
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update business identity: application/xml
## Create business identity

  Response Content Type: **application/xml**

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
