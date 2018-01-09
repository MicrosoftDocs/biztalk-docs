---
title: "sqlErrorMapping | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 403c365b-2114-4d68-89b1-6fea136f1b25
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# sqlErrorMapping
The sqlErrorMapping element contains the definition of a SQL Server error message mapped to a DRDA reply message.  
  
 \<hostIntegration.drda.sqlErrorMappings>  
\<sqlErrorMappings>  
  
## Syntax  
  
```  
<hostIntegration.drda.sqlErrorMappings>        <sqlErrorMappings>                <sqlErrorMapping>                </sqlErrorMapping>        </sqlErrorMappings></hostIntegration.drda.sqlErrorMappings>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|msSqlMessageId|xs:int|The msSqlMessageId attribute represents the identifier (ID) of the message and is a unique value across the server. This required attribute accepts an integer value.|true|n/a|  
|msSqlMessageSeverityLevel|xs:int|The msSqlMessageSeverityLevel attribute represents the severity level of the message, between 1 and 25. This required attribute accepts an integer value.|true|n/a|  
|msSqlMessageText|xs:string|The msSqlMessageText attribute represents the message text. This required attribute accepts a string value.|true|n/a|  
|drdaSqlCode|xs:int|The drdaSqlCode attribute denotes the IBM DB2 SQLCODE. This required attribute accepts an integer value.|true|n/a|  
|drdaSqlState|xs:int|The drdaSqlState attribute denotes the IBM DB2 SQLSTATE. This required attribute accepts an integer value.|true|n/a|  
|drdaReasonCode|xs:hexBinary|The drdaReasonCode attribute denotes the IBM DB2 reason code. This optional attribute accepts a hex binary value. The default value is 0.|false|n/a|  
|drdaMessageText|xs:string|The drdaMessageText attribute denotes the IBM DB2 message text. This required attribute accepts a string value.|true|n/a|  
|drdaExplanationText|xs:string|The drdaExplanationText attribute denotes the IBM DB2 explanation text. This optional attribute accepts a string value.|false|n/a|  
|drdaActionText|xs:string|The drdaActionText attribute denotes the IBM DB2 action text. This optional attribute accepts a string value.|false|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The sqlErrorMappings element contains sqlErrorMapping definition elements.|