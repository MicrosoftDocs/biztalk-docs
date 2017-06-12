---
title: "Update Schema text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 028aee6d-3f28-4513-b97d-6bc53f60d46b
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Schema: text/xml
## Update Schema (only tracking options and description)							
							
  Response Content Type: **text/xml**							
							
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
