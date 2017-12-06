---
title: "Changing the Default Values of the Security Parameters1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c926357-c90b-4ba0-a582-84d822b8db0d
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Changing the Default Values of the Security Parameters
By default, the security levels are:  
  
-   High = 168-bit encryption (minimum)  
  
-   Medium = 128-bit encryption (minimum)  
  
-   Low = 40-bit encryption (minimum)  
  
-   Unsecured = TLS/SSL fully disabled  
  
 The default values of the first three of these levels can be overridden by the following registry entries (stored in **HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services/TN3270/Parameters**):  
  
-   **SSLHighSecurity**  
  
-   **SSLMediumSecurity**  
  
-   **SSLLowSecurity**  
  
 Each registry entry will contain a numeric (DWORD) value. The registry is checked for entries only when the TN3270 server is started. For any changes in the registry entries to take effect, the TN3270 server must be restarted.  
  
## See Also  
 [Configuring Certificates](../core/configuring-certificates.md)   
 [Switching on Security and Changing Certificates](../core/switching-on-security-and-changing-certificates.md)   
 [Changing the Default Server Authentication Certificate Common Name (CN)](../core/changing-the-default-server-authentication-certificate-common-name-cn.md)