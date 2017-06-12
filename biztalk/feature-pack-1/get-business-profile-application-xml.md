---
title: "Get Business profile application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f7aca5bd-1f5e-4deb-a446-6ed385b27ec3
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Business profile: application/xml
## Get Business profile

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK

Parameters
---

Parameter|Value  |Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
partyName|(required)|Party name|path|string| 
profileName|(required)|Profile Name|path|string| 

Example Value
---

```
\<?xml version="1.0"?>
<BusinessProfile>
  <Name>string</Name>
  <Description>string</Description>
  <BusinessIdentities>
    <Description>string</Description>
    <Qualifier>string</Qualifier>
    <Value>string</Value>
    <Id>1</Id>
  </BusinessIdentities>
  <CustomSettings>
    <Name>string</Name>
    <Value>string</Value>
  </CustomSettings>
</BusinessProfile>
```