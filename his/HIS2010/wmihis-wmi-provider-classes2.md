---
title: "wmiHIS WMI Provider Classes2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75c0cff2-e077-4df5-bc39-3636d345946d
caps.latest.revision: 4
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
|[MsHis_Locale](../HIS2010/mshis-locale1.md)|Queries for locale support.|  
|[MsHis_CodePage](../HIS2010/mshis-codepage-class2.md)|Queries for code page support.|