---
title: "packageBindListener | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9c362b6-6597-4529-9460-cd36129896fa
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# packageBindListener
The packageBindListener element contains a set of attributes to define a custom bind listener.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<packageBindListeners>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <packageBindListeners>                                <packageBindListener>                                </packageBindListener>                        </packageBindListeners>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|type|xs:string|The type is Microsoft.HostIntegration.Drda.Common.PackageBindListener, which defined a DRDA Server custom bind listener.|true|n/a|  
|errorWhenNoCallback|xs:boolean|The errorWhenNoCallback attribute instructs the DRDA Service to return BGNBNDRM (Begin Bind Reply Message) to the DRDA AR client, when the custom bind listener component does not return any information on the callback interface. This optional attribute accepts a Boolean value. The default value is true.|false|true|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The packageBindListeners element contains one or more packageBindListener elements to instruct the DRDA Server to send bind package with bind SQL statement output to optional custom bind listeners.|