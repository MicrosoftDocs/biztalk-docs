---
description: "Learn about the db2ToSql element that defines the direction from DB2 to SQL Server."
title: "db2ToSql2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# db2ToSql Overview

The db2ToSql defines the direction from DB2 to SQL Server.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<dateTimeMasks>  
\<dateTimeMask>  
  
## Syntax  
  
```xml  
<hostIntegration.drdaAs.drdaService>
    <services>
         <service>
              <conversionFormats>
                   <timeMasks> 
                        <timeMask> 
                             <db2ToSql>  
                             </db2ToSql>  
                        </timeMask>    
                   </timeMasks>       
              </conversionFormats>    
         </service>   
    </services>
</hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|sourceFormat|drdaas:TimeStampFormats||true|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The dateTimeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|
