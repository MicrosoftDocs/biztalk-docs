---
title: "Scripting Using External Assemblies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Scripting functoids, warnings"
  - "Scripting functoids, external assemblies"
ms.assetid: 0bdf6adc-91b9-462e-8fd0-9cb48bfa7817
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Scripting Using External Assemblies
Scripting with external assemblies is the preferred way to use scripting in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. External assemblies provide several advantages:  
  
-   Easy code sharing  
  
-   Simpler maintenance  
  
-   Easier debugging  
  
> [!NOTE]
>  Test Map fails if the **Scripting** functoid uses an external assembly which is not registered in the GAC. It works if the external assembly is in the same bin folder as the current project's assembly (placed after build).  
  
 Re-using the script only requires setting the **Script** property of the **Scripting** functoid. Because the script is stored outside of the map, you can modify the script without changing the map. And you can use the full array of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] debugging tools to ensure your script runs correctly.  
  
> [!WARNING]
>  The code in the external assembly must be thread-safe. Under stress conditions, multiple instances of a map may be running concurrently.  
  
 For a sample function housed in an external assembly, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## See Also  
 [Scripting Functoid](../core/scripting-functoid.md)   
 [Scripting Using Inline C#, JScript .NET, and Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)   
 [Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)