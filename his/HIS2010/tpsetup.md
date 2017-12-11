---
title: "TPSETUP | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28beb67f-95d2-4d86-8f31-b96a4fff64c0
caps.latest.revision: 5
---
# TPSETUP
TPSETUP is a program that simplifies the setting of registry or environment variables needed by autostarted invokable TPs. Without an interface like that provided by TPSETUP, configuring such variables can be complicated and error prone. Therefore, it is recommended that you use code like TPSETUP in installation programs for autostarted invokable TPs.  
  
## Operation  
 INSTALL.C, the source code for TPSETUP, can be compiled to work in Microsoft Windows.  
  
 We recommend that autostarted invokable TPs be written as Windows services. To create the installation program for such TPs, study the code in INSTALL.C. For example, use the **CreateService** function or similar code when installing a TP that will run as a service under Windows. (For important information about how services work under Windows, see the documentation for Windows.)  
  
## See Also  
 [APPC Samples](../HIS2010/appc-samples.md)