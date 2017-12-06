---
title: "hostIntegration.drda.sqlErrorMappings | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efb6101a-260c-4dbf-b684-b6b4885cd53c
caps.latest.revision: 2
ms.author: "dwrede"
author: MandiOhlinger
manager: anneta
---
# hostIntegration.drda.sqlErrorMappings
The DRDA Service converts SQL Server error codes and messages to instances of a DRDA reply message or a DB2 SQL Communications Area based on a defined set of mappings stored in an MsDrdaErrorMappings.xml file in the program system directory. The inbound SQL Server error code is mapped to the outbound DRDA DB2 error code.  
  
## Syntax  
  
```  
<hostIntegration.drda.sqlErrorMappings></hostIntegration.drda.sqlErrorMappings>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The sqlErrorMappings element contains sqlErrorMapping definition elements.|1 to 1|  
  
### Parent Elements  
 None