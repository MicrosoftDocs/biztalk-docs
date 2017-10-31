---
title: "securityManager | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11bd7092-21fa-4fb4-833a-904ce2678ae3
caps.latest.revision: 2
ms.author: "dwrede"
---
# securityManager
The securityManager element contains the security settings  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <securityManager>                        </securityManager>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|type|xs:string|The securityManager type is the Microsoft.HostIntegration.Drda.Server.SecurityManager, which processes authentication of in-bound TCP/IP network connections.|true|n/a|  
|securityTokenTimeout|xs:duration|The securityTokenTimeout attribute instructs the DRDA Server to retain a security token for a duration of time, after which to obtain a new Windows Client Identifier (CID). This optional attribute accepts a duration value. The default value is PT8H (period of time is 8 hours). The duration value is specified in the form PnYnMnDTnHnMnS.          • P  indicates the Period of time for the duration (required)          • nY indicates the number of years          • nM indicates the number of months          • nD indicates the number of days          • T  indicates the start of a time section (required if you are going to specify hours, minutes, or seconds)          • nH indicates the number of hours          • nM indicates the number of minutes          • nS indicates the number of seconds|false|P1D|  
|authenticationLookupTimeout|xs:duration|The authenticationLookupTimeout attribute instructs the DRDA Server the duration of time to wait for a security authentication lookup request before failing. This optional attribute accepts a duration value. The default value is PT30S (Period of Time is 30 seconds). The duration value is specified in the form PnYnMnDTnHnMnS.          • P  indicates the Period of time for the duration (required)          • nY indicates the number of years          • nM indicates the number of months          • nD indicates the number of days          • T  indicates the start of a time section (required if you are going to specify hours, minutes, or seconds)          • nH indicates the number of hours          • nM indicates the number of minutes          • nS indicates the number of seconds|false|PT30S|  
|authenticationLookupRetries|xs:int|The authenticationLookupRetries attribute instructs the DRDA Server the number of times to attempt a security authentication lookup request before failing. This optional attribute accepts an integer value. The default value is 3 retries.|false|3|  
|mappedAuthenticationDomain|xs:string|The mappedAuthenticationDomain attribute instructs the DRDA Service to which Microsoft Windows Active Directory domain to map the in-bound DRDA client credentials (user name and password), when connecting to SQL Server configured for Windows authentication using integrated Security Support Provider Interface (SSPI), but not when using Microsoft Enterprise Single Sign-On. This optional attribute accepts a string value. The default value is an empty string.|false|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|