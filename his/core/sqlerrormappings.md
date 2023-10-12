---
description: "Learn more about: sqlErrorMappings"
title: "sqlErrorMappings"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# sqlErrorMappings
The sqlErrorMappings element contains sqlErrorMapping definition elements.  
  
 \<hostIntegration.drda.sqlErrorMappings>  
  
## Syntax  
  
```  
<hostIntegration.drda.sqlErrorMappings>        <sqlErrorMappings>        </sqlErrorMappings></hostIntegration.drda.sqlErrorMappings>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The sqlErrorMapping element contains the definition of a SQL Server error message mapped to a DRDA reply message.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The DRDA Service converts SQL Server error codes and messages to instances of a DRDA reply message or a DB2 SQL Communications Area based on a defined set of mappings stored in an MsDrdaErrorMappings.xml file in the program system directory. The inbound SQL Server error code is mapped to the outbound DRDA DB2 error code.|
