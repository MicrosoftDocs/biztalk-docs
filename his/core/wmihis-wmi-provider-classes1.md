---
description: "Learn more about: wmiHIS WMI Provider Classes"
title: "wmiHIS WMI Provider Classes1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# wmiHIS WMI Provider Classes
Microsoft® Host Integration Server provider supplies information regarding the configuration of Host Integration Server. As an instance provider, the wmiHIS provider implements the standard **IWbemProviderInit** interface and the following **IWbemServices** methods:  
  
- **CreateInstanceEnumAsync**  
  
- **DeleteInstanceAsync**  
  
- **GetObjectAsync**  
  
- **PutInstanceAsync**  
  
  For more information on **IWbemProviderInit** and **IWbemServices**, see [COM API for WMI](/windows/win32/wmisdk/com-api-for-wmi).  
  
  You can access the WmiHIS provider classes in the \root\MicrosoftHIS namespace.  
  
|Class|Description|  
|-----------|-----------------|  
|[MsHis_Locale](../core/mshis-locale2.md)|Queries for locale support.|  
|[MsHis_CodePage](../core/mshis-codepage-class1.md)|Queries for code page support.|