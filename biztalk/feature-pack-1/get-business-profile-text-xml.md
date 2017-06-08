---
title: "Get Business profile text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 6c79f36f-201d-45a9-8f83-044c4d66b73d
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Business profile: text/xml
## Get Business profile

  Response Content Type: **text/xml**

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