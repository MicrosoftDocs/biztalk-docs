---
title: "Update Schema application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 922010b3-df97-4bd5-8c46-925238ca5842
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Schema: application/xml
## Update Schema (only tracking options and description)							
							
  Response Content Type: **application/xml**							
							
## *Parameters*							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**schemaName** |(required)|Schema Name|path|  |  							
**schema** |(required)||body|string|		

schemaName Data Type

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
										
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
