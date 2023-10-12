---
description: "Learn more about: applicationEncodings"
title: "applicationEncodings"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# applicationEncodings
The applicationEncodings element contains applicationEncoding elements for specifying default application-level encoding schemes on a per-database basis.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <applicationEncodings>                        </applicationEncodings>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The applicationEncodings type is Microsoft.HostIntegration.ConfigurationSectionHandlers, which defines  application-level encoding schemes and conversions.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|
