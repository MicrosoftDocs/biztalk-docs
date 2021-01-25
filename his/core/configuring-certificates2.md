---
description: "Learn more about: Configuring Certificates"
title: "Configuring Certificates2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b64e0083-bff1-431a-9828-3af6adcc6f59
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring Certificates
The **TN3270 Server properties** dialog box contains a **Port/Security** tab, which allows you to configure the ports to be available to the TN3270 server. The security parameters are then configured on a port-by-port basis.  
  
 The following issues are required to implement security support:  
  
-   A client that attempts to connect to a port that has not been configured on the TN3270 server will be unsuccessful.  
  
-   The default port defined in SNA Manager does not affect the security configuration. Either a port security record is found (in which case it is used), or it is not found (in which case the client fails to connect).  
  
-   A port with security level Unsecured means that TLS/SSL will be fully disabled on that port. There will be no exchange of certificates on that port.  
  
-   All the changes made to the configuration are dynamic.  
  
-   Server authentication certificates may not be dynamically changed.  
  
## In This Section  
 [Switching on Security and Changing Certificates](../core/switching-on-security-and-changing-certificates1.md)  
  
 [Changing the Default Values of the Security Parameters](../core/changing-the-default-values-of-the-security-parameters1.md)  
  
 [Changing the Default Server Authentication Certificate Common Name (CN)](../core/changing-the-default-server-authentication-certificate-common-name-cn-2.md)
