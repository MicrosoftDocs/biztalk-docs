---
title: "Create SendPortGroup application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 06cdf3b2-fbd0-46df-9258-4ac50ae87b05
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create SendPortGroup: application/xml
## Create SendPortGroup

  Response Content Type: **application/xml**

## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**sendPortGroup** |(required)||body|     |  					

### Data Type

```
\<?xml version="1.0"?>
<SendPortGroup>
  <Name>string</Name>
  <SendPorts>string</SendPorts>
  <CustomData>string</CustomData>
  <Filter>string</Filter>
  <Status>string</Status>
  <ApplicationName>string</ApplicationName>
  <Description>string</Description>
</SendPortGroup>

```


		

## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
