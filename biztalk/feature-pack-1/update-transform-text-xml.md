---
title: "Update Transform text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f0bac664-37b7-437d-8b9e-ffebc727ad74
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update Transform: text/xml
## Update Transform. Only Description can be edited							
							
  Response Content Type: **text/xml**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**transformFullName** |(required)|Transform full name|path|string   |  							
**transform** |||body||							
Data Type transform

```
\<?xml version="1.0"?>
<Transform>
  <FullName>string</FullName>
  <ApplicationName>string</ApplicationName>
  <Description>string</Description>
  <Assembly>string</Assembly>
  <SourceSchema>string</SourceSchema>
  <TargetSchema>string</TargetSchema>
  <XmlContent>string</XmlContent>
</Transform>

```
					
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
