---
title: "applicationEncoding | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3758bdd-3209-45e2-ba8a-8f988072a9cb
caps.latest.revision: 2
ms.author: "dwrede"
author: MandiOhlinger
manager: anneta
---
# applicationEncoding
The applicationEncodings type is Microsoft.HostIntegration.ConfigurationSectionHandlers, which defines  application-level encoding schemes and conversions.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<applicationEncodings>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <applicationEncodings>                                <applicationEncoding>                                </applicationEncoding>                        </applicationEncodings>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|scheme|drdaas:ApplicationEncodingSchemes|The scheme attribute instructs the DRDA Service to encode output parameter and result set values using an override encoding scheme, and not the DRDA AR client-requested encoding scheme. This optional attribute accepts a string value. The supported values are Ebcdic, Unicode, and Ansi. The default value is Unicode.|true|n/a|  
|ccsid|drdaas:ApplicationEncodingCcsids|The ccsid attribute instructs the DRDA Service to encode output parameter and result set values using an override CCSID (Coded Character Set Identifier), and not the DRDA AR client-requested CCSID. This optional attribute accepts an integer. The default value is 1208. The schema includes a list of pre-defined CCSID values.|true|n/a|  
|customCcsid|xs:int|A Coded Character Set Identifier that is to be used and is not in the predefined list.|false|-1|  
|database|xs:string|The database attribute instructs the DRDA Service to encode output parameter and result set values using an override encoding scheme, and not the DRDA AR client-requested encoding scheme, for a specified target SQL Server database only. This optional attribute accepts a string value. The default value is an empty string.|true|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The applicationEncodings element contains applicationEncoding elements for specifying default application-level encoding schemes on a per-database basis.|