---
description: "Learn more about: Workstation Authentication"
title: "Workstation Authentication1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Workstation Authentication
When you receive a request from a source that is external to the corporate network containing the SNA subdomain, or if you are not using a domain-type network, domain authentication is usually difficult to implement.  
  
 In this case, Host Integration Server performs workstation authentication on the following services:  
  
- TN3270 terminal access  
  
- TN5250 terminal access  
  
- 3270 access from terminal emulators connecting through Host Integration Server client software  
  
  For these services, you can specify a list of allowed client workstation IP addresses for defined resources. When Host Integration Server receives a session request, it determines whether the requesting IP (or workstation name for TN3270E connections) matches that specified for the requested resource. Once verified, Host Integration Server allows the request to proceed.  
  
> [!NOTE]
>  This type of authentication is not as secure as domain security because workstation names and the IP address are transmitted in clear text over the network.  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)   
 [Authentication](../core/authentication1.md)   
 [Domain Authentication](../core/domain-authentication2.md)
