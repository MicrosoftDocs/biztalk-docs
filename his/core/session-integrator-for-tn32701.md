---
title: "Session Integrator for TN32701 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5e52fe3-2f74-4cbc-b706-4a702bbb8bc9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Session Integrator for TN3270
Session Integrator can be used to interact with TN3270 sessions. The behavior for Session Integrator using the TN3270 protocol is the same as Session Integrator for LU2 except for a different connection setting.  
  
 **Connection string for TN3270 sessions**  
  
 **Transport** – TN3270 – Indicates that Session Integrator should use the TN3270 protocol.  
  
 **TN3270SERVER** – The IP address or IP Host name of the TN3270 server.  
  
 **TN3270PORT** – The IP port on which the TN3270 server is listening.  
  
 The typical ports would be port 23 for non-SSL and port 992 for SSL/TLS.  
  
 **DEVICETYPE** – Indicates the 3270 terminal type to be emulated. The typical value would be IBM-3278-2.  
  
 **SECURITY** - Indicates the type of security used for the connection.  
  
- NONE- The connection is not encrypted.  
  
- TLS1- The connection negotiates encryption using TLS v1.0.  
  
  **CERTIFICATECHECK** – Indicates how the certificate is verified if security is set to TLS1.  
  
- NONE- The data is encrypted, but the server certificate is not verified.  
  
- VERIFIED- The server certificate will be verified by the Schannel security support provider during the TLS negotiation.  
  
```  
m_Handler.Connect("TRANSPORT=TN3270;TN3270SERVER=SYS1;TN3270Port=23;DeviceType=IBM-3278-2;SECURITY=TLS1;CERTIFICATECHECK=VERIFIED”);  
```  
  
 **SessionConnectionDisplay**  
  
 **Security** [enum] – Indicates the type of security used for the connection.  
  
- TNSecurity.None- The connection is not encrypted.  
  
- TNSecurity.TLS1- The connection negotiates encryption using TLS v1.0.  
  
  **CertificateCheck** [enum] - Indicates how the certificate is verified if security is set to TLS1.  
  
- TNCertificateCheck .None-The data is encrypted, but the server certificate is not verified.  
  
- TNCertificateCheck .Verified-The server certificate will be verified by the Schannel security support provider during the TLS negotiation.  
  
## See Also  
 [Working with Session Integrator](../core/working-with-session-integrator1.md)