---
title: "Protecting the TI .NET Assembly from Unauthorized Access1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb0bfb7e-08a4-41dc-81cc-22e5ed3bcd99
caps.latest.revision: 4
---
# Protecting the TI .NET Assembly from Unauthorized Access
To prevent an attacker from viewing or modifying the contents of a Transaction Integrator (TI) .NET assembly and then using that information to either create a client application which spoofs the identity of an authorized user or modify the custom properties of the component, you should:  
  
-   Place the computer that is running Visual Studio and TI Designer in a secure location.  
  
-   Confirm that the access permissions to Visual Studio, TI Designer, or any other tool used to modify TI type libraries and .NET assemblies are set correctly.  
  
-   Store all TI .NET assemblies in a secure directory.  
  
-   Confirm that the access permissions are set correctly on all .NET assemblies.  
  
-   Confirm that the access permissions are set correctly on the directory that contains the .NET assemblies.  
  
## See Also  
 [Protecting the Output from Tracing and Network Monitoring Activities](../HIS2010/protecting-the-output-from-tracing-and-network-monitoring-activities1.md)   
 [Protecting the TI Record or Playback Files from Unauthorized Access](../HIS2010/protecting-the-ti-record-or-playback-files-from-unauthorized-access2.md)   
 [Threat Mitigation within Visual Studio &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/16f1392e-f1e6-44f7-9db7-213625c38897)