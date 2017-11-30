---
title: "Changing the Default Server Authentication Certificate Common Name (CN)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11fe319-01f3-4248-bb81-552d3782ecb0
caps.latest.revision: 3
---
# Changing the Default Server Authentication Certificate Common Name (CN)
By default, the TN3270 server will look for a certificate with a common name that matches its host name, for example, the name returned by **gethostname**. This can be changed by the following registry entry (stored in **HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services/TN3270/Parameters**):  
  
-   **SSLServerCertCN**  
  
 This entry contains a string containing the new CN for the certificate. The registry is checked for entries only when the TN3270 server is started. For any changes in the registry entries to take effect, the TN3270 server must be restarted.  
  
## See Also  
 [Configuring Certificates](../HIS2010/configuring-certificates1.md)   
 [Switching on Security and Changing Certificates](../HIS2010/switching-on-security-and-changing-certificates2.md)   
 [Changing the Default Values of the Security Parameters](../HIS2010/changing-the-default-values-of-the-security-parameters2.md)