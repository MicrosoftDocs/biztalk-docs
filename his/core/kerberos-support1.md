---
description: "Learn more about: Kerberos Support"
title: "Kerberos Support1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Kerberos Support
In addition to NTLM, Kerberos support is now available. To use Kerberos support, it is necessary to set a Service Principal Name (SPN) for each server in the subdomain. You can do this through the command line as follows:  
  
```  
setspn -a hisservice/servername serviceaccount  
```  
  
 An icon will appear in the status bar to verify that the system is using Kerberos. Kerberos support is compatible with previous versions of Host Integration Server.  
  
## See Also  
 [Command-Line Interface](../core/command-line-interface2.md)
