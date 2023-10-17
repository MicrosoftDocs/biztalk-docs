---
description: "Learn more about: JMS MQRFH2 Sample Dependencies and Strong Key Name Definition"
title: "JMS MQRFH2 Sample Dependencies and Strong Key Name Definition"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# JMS MQRFH2 Sample Dependencies and Strong Key Name Definition
The Visual Studio project ESB.JMS.PipelineComponents depends on the following folder:  
  
-   \<BizTalk Server Installation Directory\>. This folder provides access to the following namespaces:  
  
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
