---
title: "drdaServiceTraceListener | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb2bca9c-8b0d-46e1-a3a8-be002defcbcb
caps.latest.revision: 2
ms.author: "dwrede"
author: MandiOhlinger
manager: anneta
---
# drdaServiceTraceListener
The drdaServiceTraceListener element contains a set of attributes to define a custom trace listener.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<drdaServiceTraceListeners>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <drdaServiceTraceListeners>                                <drdaServiceTraceListener>                                </drdaServiceTraceListener>                        </drdaServiceTraceListeners>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|type|xs:string|The type is Microsoft.HostIntegration.Drda.Common.BaseDrdaTraceListener, which defined a DRDA Server custom trace listener.|true|n/a|  
|traceLevel|xs:int|The traceLevel attribute instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This optional attribute accepts an integer value. The default value is -1, which disables tracing.|false|-1|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The drdaServiceTraceListeners element contains one or more drdaServiceTraceListener elements to instruct the DRDA Server to send trace output to optional custom text trace listeners.|