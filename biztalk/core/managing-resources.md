---
title: "Manage Resources | Microsoft Docs"
description: Use btstask or BizTalk Administration to work with assemblies, scripts, certificates, binding files, and more in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b478ef2e-1363-4c2c-a4b7-6a582a6b33a5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage Resources

## Overview
The topics in this section provide instructions on how to use the BizTalk Server Administration console or the BTSTask command-line tool to manage BizTalk Server resources after they have been deployed into a BizTalk group. Resources include the following types of artifacts:  
  
-   BizTalk Assemblies  
  
-   Pre- and post-processing scripts  
  
-   .NET assemblies  
  
-   COM components  
  
-   Certificates  
  
-   Ad hoc files  
  
-   BAM definitions  
  
-   Binding files  
  
-   Virtual directories  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
> 
> [!NOTE]
>  Do not add multiple resources with the same name, regardless of case, to a BizTalk Server group. Adding multiple resources with the same name to a BizTalk Server group is not supported, even when the BizTalk Server management database is housed on a SQL Server that is configured to use binary collation and supports case sensitivity.  
  
## Next steps
  
-   [Managing BizTalk Assemblies](../core/managing-biztalk-assemblies.md)  
  
-   [Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md)  
  
-   [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)  
  
-   [Refresh a Resource](../core/how-to-refresh-a-resource.md)