---
description: "Learn more about: ListTypes Command"
title: "ListTypes Command | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94febe8a-4c1e-4581-a6d1-ef579633e745
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ListTypes Command
Lists all of the artifact types that you can add to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the **AddResource** command. For more information about the **AddResource** command, see [AddResource Command](../core/addresource-command.md).  
  
 The fully qualified names of the supported artifact types are as follows:  
  
-   .NET assembly: System.BizTalk:Assembly  
  
-   BAM definition: System.BizTalk:Bam  
  
-   BizTalk assembly: System.BizTalk:BizTalkAssembly  
  
-   BizTalk binding file: System.BizTalk:BizTalkBinding  
  
-   Security certificate: System.BizTalk:Certificate  
  
-   COM component: System.BizTalk:Com  
  
-   Ad hoc file: System.BizTalk:File  
  
-   Postprocessing script: System.BizTalk:PostProcessingScript  
  
-   Preprocessing script: System.BizTalk:PreProcessingScript  
  
-   Policy or rule: System.BizTalk:Rules  
  
-   Virtual directory: System.BizTalk:WebDirectory  
  
> [!NOTE]
>  To avoid namespace conflicts, you should always use the full type name (such as System.BizTalk:Assembly) rather than the type name alone (such as Assembly).  
  
## Usage  
 **BTSTask ListTypes**  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)
