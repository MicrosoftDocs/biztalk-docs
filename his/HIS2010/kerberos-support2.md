---
title: "Kerberos Support2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d453767-78d2-484f-a3a1-55f7a9e36121
caps.latest.revision: 4
---
# Kerberos Support
In addition to NTLM, Kerberos support is now available. To use Kerberos support, it is necessary to set a Service Principal Name (SPN) for each server in the subdomain. You can do this through the command line as follows:  
  
```  
setspn -a hisservice/servername serviceaccount  
```  
  
 An icon will appear in the status bar to verify that the system is using Kerberos. Kerberos support is compatible with previous versions of Host Integration Server.  
  
## See Also  
 [Command-Line Interface](../HIS2010/command-line-interface1.md)