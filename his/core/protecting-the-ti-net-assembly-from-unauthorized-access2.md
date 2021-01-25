---
description: "Learn more about: Protecting the TI .NET Assembly from Unauthorized Access"
title: "Protect the TI .NET Assembly from Unauthorized Access | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37b0ad05-29d5-4a7f-8336-c9af6e89f033
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Protecting the TI .NET Assembly from Unauthorized Access

## Overview
To prevent an attacker from viewing or modifying the contents of a Transaction Integrator (TI) .NET assembly and then using that information to either create a client application which spoofs the identity of an authorized user or modify the custom properties of the component, you should:  
  
-   Place the computer that is running Visual Studio and TI Designer in a secure location.  
  
-   Confirm that the access permissions to Visual Studio, TI Designer, or any other tool used to modify TI type libraries and .NET assemblies are set correctly.  
  
-   Store all TI .NET assemblies in a secure directory.  
  
-   Confirm that the access permissions are set correctly on all .NET assemblies.  
  
-   Confirm that the access permissions are set correctly on the directory that contains the .NET assemblies.  
  
## See Also  
 [Protecting the Output from Tracing and Network Monitoring Activities](../core/protecting-the-output-from-tracing-and-network-monitoring-activities2.md)   
 [Protecting the TI Record or Playback Files from Unauthorized Access](../core/protecting-the-ti-record-or-playback-files-from-unauthorized-access1.md)   
