---
title: "Get a schemas by name text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: a8db9574-a673-4665-a3e7-7221f3308980
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get a schemas by name: text/xml
## GET a schemas by name.  
  
  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK


## *Parameters*	
Parameter  |Value  |Description  |Parameter Type  |Data Type  	
---------|---------|---------|---------|---------| 	
**schemaName**|  (required)       | Name of the schema.|path  |  string | 	

## Example Value

```
\<?xml version="1.0"?>
<Schema>
  <Name>string</Name>
  <TargetNameSpace>string</TargetNameSpace>
  <RootName>string</RootName>
  <ApplicationName>string</ApplicationName>
  <AssemblyName>string</AssemblyName>
  <SchemaType>string</SchemaType>
  <Description>string</Description>
  <Tracking>
    <TrackedProperties>
      <PropertyName>string</PropertyName>
      <TrackingEnabled>true</TrackingEnabled>
    </TrackedProperties>
  </Tracking>
</Schema>
```
