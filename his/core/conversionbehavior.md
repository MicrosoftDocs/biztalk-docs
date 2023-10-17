---
description: "Learn more about: conversionBehavior"
title: "conversionBehavior"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# conversionBehavior
The conversionBehavior element is for use by Transaction Integrator only. The DRDA Service does not require this element.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <conversionBehavior>                        </conversionBehavior>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|acceptBadCOMP3Sign|xs:boolean|Instructs Transaction Integrator primitive conversion routines to accept Bad Sign in a COMP3 data value.|false|false|  
|acceptNullPacked|xs:boolean|Instructs Transaction Integrator primitive conversion routines to accept null values in Windows Data type during pack operations.|false|false|  
|acceptNullZoned|xs:boolean|Instructs Transaction Integrator primitive conversion routines to accept null Zoned Numeric data types during unpack operations.|false|false|  
|stringsAreNullTerminatedAndSpacePadded|xs:boolean|Instructs Transaction Integrator primitive conversion routines to use space padding when converting strings to COBOL types and use to null termination on unpack.|false|false|  
|alwaysCheckForNull|xs:boolean|Instructs Transaction Integrator primitive conversion routines to always check for a null on a Windows string when converting to COBOL PIC X data type.|false|false|  
|trimTrailingNulls|xs:boolean|Instructs Transaction Integrator primitive conversion routines to remove trailing nulls when packing a Windows string COBOL PIC X data type.|false|false|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|
