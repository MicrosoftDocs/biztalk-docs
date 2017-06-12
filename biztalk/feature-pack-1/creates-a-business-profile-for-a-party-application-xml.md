---
title: "Creates a business profile for a party application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ca311011-ccc5-4320-b3ce-67b483d96892
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Creates a business profile for a party: application/xml
## Creates a business profile for a party

  Response Content Type: **application/xml**


Parameters
---



Parameter|Value|Description|Parameter Type|Data Type 
---------|---------|---------|---------|---------
businessProfile|(required)|The business profile.|body|        | 
partyName|(required)|Party name.|path|string| 


Response Messages
---



HTTP Status Code|Reason|Response Model|Headers  
---------|---------|---------|---------
204|No Content |         |        | 

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