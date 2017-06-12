---
title: "Update specific SendPortGroup application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: fa68e4e4-6801-441c-a58a-d88f68ec050a
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update specific SendPortGroup: application/xml
## Update specific SendPortGroup	
							
  Response Content Type: **application/xml**							
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**sendPortGroup** |(required)|Details of SendPortGroup|body||  							
**sendPortGroupName** |(required)|SendPortGroup Name|path|string|		

### Data Type

```
<?xml version="1.0"?> <SendPortGroup> <Name>string</Name> <SendPorts>string</SendPorts> <CustomData>string</CustomData> <Filter>string</Filter> <Status>string</Status> <ApplicationName>string</ApplicationName> <Description>string</Description> </SendPortGroup>
```

					
						
							
## Response Messages							
							
							
HTTP Status Code  |Reason  |Response Model  |Headers  							
---------|---------|---------|---------							
204     |  No Content       |         |        |							
