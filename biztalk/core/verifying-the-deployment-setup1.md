---
title: "Verifying the Deployment Setup1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CLASSPATH, verifying"
  - "deployment, verifying setup"
ms.assetid: 6c719e4c-9a61-480f-a4e4-0a1c518d1364
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Verifying the Deployment Setup
Before you use the BizTalk Server to import a binding file, you must verify the following:  
  
-   The CLASSPATH is pointing to a specific location for the JD Edwards EnterpriseOne-specific files. Verify that the location of these files is the same on the new computer, or edit the binding file.  
  
-   The folders for the responses exist and are identical on the new computer, or edit the binding file.  
  
-   JD Edwards EnterpriseOne system passwords, if present in the configuration, are saved as ***** in the binding file. For more information see [Deployment Limitations](../core/deployment-limitations4.md).  
  
## See Also  
 [Deploying Ports and Assemblies](../core/deploying-ports-and-assemblies3.md)