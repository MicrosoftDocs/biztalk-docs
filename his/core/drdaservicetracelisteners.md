---
description: "Learn more about: drdaServiceTraceListeners"
title: "drdaServiceTraceListeners"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# drdaServiceTraceListeners
The drdaServiceTraceListeners element contains one or more drdaServiceTraceListener elements to instruct the DRDA Server to send trace output to optional custom text trace listeners.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <drdaServiceTraceListeners>                        </drdaServiceTraceListeners>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
 None  
  
### Child Elements  
  
|Element|Description|Occurrence Constraint|  
|-------------|-----------------|---------------------------|  
||The drdaServiceTraceListener element contains a set of attributes to define a custom trace listener.|1|  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|
