---
title: "Create business identity text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ad778eed-eb74-46f8-a2e0-e6c47393fa18
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create business identity: text/xml
## Create business identity

  Response Content Type: **text/xml**

Parameters
---


Parameter|Value  |Description |Parameter Type|Data Type  
---------|---------|---------|---------|---------
qualifierIdentity|(required)|Qualifier identity details|body|         |
partyName|(required)|Party name|path|string|
profileName|(required)|Profile name|path|string|

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