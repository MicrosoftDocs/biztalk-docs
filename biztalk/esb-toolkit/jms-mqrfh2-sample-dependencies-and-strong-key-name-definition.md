---
title: "JMS MQRFH2 Sample Dependencies and Strong Key Name Definition | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3a5cdce-dcdf-48df-91a5-8cf2afce9255
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# JMS MQRFH2 Sample Dependencies and Strong Key Name Definition
The [!INCLUDE[vs2010](../includes/vs2010-md.md)] project ESB.JMS.PipelineComponents depends on the following folder:  
  
-   \<BizTalk Server Installation Directory>. This folder provides access to the following namespaces:  
  
    -   **Microsoft::BizTalk::Message::Interop**  
  
    -   **Microsoft::BizTalk::Component::Interop**  
  
## The Strong Name Key Definition  
 Usually, the strong-name key definition resides in the AssemblyInfo.cpp file. However, this would conflict with the C++ manifest file that the compiler adds to the assembly after it reads the AssemblyInfo.cpp file. This conflict would prevent any attempt to place the file in the global assembly cache. Instead, the linker controls the strong name key file by specifying the key file located at ../../../../../../Keys/Microsoft.Practices.ESB.snk. To edit this value, navigate to the following option setting:  
  
 ESB.JMS.Schemas  
  
 \- Project  
  
 \- - Properties  
  
 \- - - Configuration Properties  
  
 \- - - - Linker  
  
 \- - - - - Advanced  
  
 \- - - - - - Key File  
  
> [!NOTE]
>  If you construct a JMS Pipeline Component, you must edit the AssemblyInfo.cpp file to remove any references to the strong-name key file, as described earlier. After you do that, edit the **Key File** option in the advanced properties of the Linker to specify the path and name of the strong-name key file.