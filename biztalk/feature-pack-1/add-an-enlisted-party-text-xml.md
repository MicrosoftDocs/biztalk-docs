---
title: "Add an enlisted party text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 5dc09295-fb92-4942-b80f-994a084b8989
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Add an enlisted party: text/xml
## Add an enlisted party

  Response Content Type: **text/xml**

## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**enlistedParties** |(required)|list of Enlisted party details|body|    |  							
**applicationName** |(required)|Application name|path|string|							
**roleLinkName**    |(required)|Role link name|path|string|					

## Example Value

```
\<?xml version="1.0"?>
<EnlistedParty>
  <Name>string</Name>
  <Mappings>
    <PortTypeName>string</PortTypeName>
    <OperationName>string</OperationName>
    <SendPort>string</SendPort>
  </Mappings>
</EnlistedParty>

```
		
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
