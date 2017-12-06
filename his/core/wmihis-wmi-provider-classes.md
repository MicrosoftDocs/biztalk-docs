---
title: "wmiHIS WMI Provider Classes1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8186c2b1-bf9c-4dd9-af8d-ec6fd7153f21
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# wmiHIS WMI Provider Classes
Microsoft® Host Integration Server provider supplies information regarding the configuration of Host Integration Server. As an instance provider, the wmiHIS provider implements the standard **IWbemProviderInit** interface and the following **IWbemServices** methods:  
  
-   **CreateInstanceEnumAsync**  
  
-   **DeleteInstanceAsync**  
  
-   **GetObjectAsync**  
  
-   **PutInstanceAsync**  
  
 For more information on **IWbemProviderInit** and **IWbemServices**, see "COM API for WMI" in the MSDN Library at http://msdn.microsoft.com/library.  
  
 You can access the WmiHIS provider classes in the \root\MicrosoftHIS namespace.  
  
|Class|Description|  
|-----------|-----------------|  
|[MsHis_Locale](../core/mshis-locale.md)|Queries for locale support.|  
|[MsHis_CodePage](../core/mshis-codepage-class.md)|Queries for code page support.|