---
title: "Error Code Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 719997da-0185-4a2a-af42-c23d8f24cdbb
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error Code Mappings
The DRDA Service converts SQL Server error codes and messages to instances of a DRDA reply message or a DB2 SQLCA (Communications Area) based on a defined set of mappings stored in an MsDrdaErrorMappings.xml file in the %DRDAROOT%\system directory. The in-bound SQL Server error code is mapped to the out-bound DB2 error code. The XML document contains a set standard format, as documented in the associated HostIntegrationDrdaSqlErrorMappings.xsd schema file.  
  
```  
<SqlErrorMappings>  
<sqlErrorMapping  
msSqlMessageId="201"   
msSqlMessageSeverityLevel="16"  
msSqlMessageText="Procedure or function '{0}' expects parameter '{1}', which was not supplied."  
drdaSqlCode="-313"  
drdaSqlState="07001"  
drdaReasonCode=""  
drdaMessageText="THE NUMBER OF HOST VARIABLES SPECIFIED IS NOT EQUAL TO THE NUMBER OF PARAMETER MARKERS."  
drdaExplanationText="The server cannot execute a SQL statement that contains an incorrect parameter list."  
drdaActionText="Verify the number and type of parameters."  
/>  
  
```  
  
 Example. SQL Server error message mapped to DB2 error message.  
  
 The following table shows Microsoft SQL Server error messages.  
  
||||  
|-|-|-|  
|Item|Type|Description|  
|sqlErrorMappings|element|The sqlErrorMappings element contains sqlErrorMapping definition elements.|  
|sqlErrorMapping|element|The sqlErrorMapping element contains the definition of a SQL Server error message mapped to a DRDA reply message.|  
  
 The following table shows Microsoft SQL Server error messages.  
  
||||  
|-|-|-|  
|Item|Type|Description|  
|msSqlMessageId|integer|The msSqlMessageId attribute represents the identifier (ID) of the message and is a unique value across the server. This required attribute accepts an integer value.|  
|msSqlMessageSeverityLevel|integer|The msSqlMessageSeverityLevel attribute represents the severity level of the message, between 1 and 25. This required attribute accepts an integer value.|  
|msSqlMessageText|string(1024)|The msSqlMessageText attribute represents the message text. This required attribute accepts a string value.|  
  
 The following table shows IBM DB2 error messages.  
  
||||  
|-|-|-|  
|Item|Type|Description|  
|drdaSqlCode|integer|The drdaSqlCode attribute denotes the IBM DB2 SQLCODE. This required attribute accepts an integer value.|  
|drdaSqlState|integer|The drdaSqlState attribute denotes the IBM DB2 SQLSTATE. This required attribute accepts an integer value.|  
|drdaReasonCode|hex binary|The drdaReasonCode attribute denotes the IBM DB2 reason code. This optional attribute accepts a hex binary value. The default value is 0.|  
|drdaMessageText|string|The drdaMessageText attribute denotes the IBM DB2 message text. This required attribute accepts a string value.|  
|drdaExplanationText|string|The drdaExplanationText attribute denotes the IBM DB2 explanation text. This optional attribute accepts a string value.|  
|drdaActionText|string|The drdaActionText attribute denotes the IBM DB2 action text. This optional attribute accepts a string value.|