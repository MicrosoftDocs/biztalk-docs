---
title: "Protect the Tracing and Network Monitoring output | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21048daf-1093-4c91-a08d-20811ae93312
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Protecting the Output from Tracing and Network Monitoring Activities

## Overview
To prevent an attacker from viewing the user credential information that might be stored in trace files or network monitoring files, you should:  
  
-   Confirm that only authorized users are allowed to run the SNA TRACE or Microsoft Network Monitoring programs on the computer that is running Transaction Integrator.  
  
-   Store all tracing (Tracebits) output files and network monitoring (Netmon) output files in a secure directory.  
  
-   Confirm that the access permissions are set correctly on all tracing output files and network monitoring output files.  
  
-   Confirm that the access permissions are set correctly on the directory that contains the output files.  
  
-   Delete all tracing output files and network monitoring output files as soon as you are done with them.  
  
## See Also  
 [Protecting the TI .NET Assembly from Unauthorized Access](../core/protecting-the-ti-net-assembly-from-unauthorized-access2.md)   
 [Protecting the TI Record or Playback Files from Unauthorized Access](../core/protecting-the-ti-record-or-playback-files-from-unauthorized-access1.md)   