---
title: "Update specific SendPortGroup text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: bf5d2012-b727-4f40-86af-d1d1362527e6
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update specific SendPortGroup: text/xml
## Update specific SendPortGroup	
							
  Response Content Type: **text/xml**							
							
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
