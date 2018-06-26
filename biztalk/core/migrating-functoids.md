---
title: "Migrating Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoids, migrating"
  - "migrating, maps"
  - "Migrating functoids, about Migrating functoids"
  - "Migrating functoids"
  - "Scripting functoids"
  - "migrating, functoids"
  - "migrating, Scripting functoids"
ms.assetid: fc5b3ac9-28c6-41df-b779-15a8c3188528
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Migrating Functoids
When you migrate a map from previous versions of BizTalk Server to BizTalk Server, any functoids included in the map are also migrated. If the functoids you migrate do not include **Scripting** functoids, no additional migration tasks are required. However if your map includes **Scripting** functoids or custom functoids, you may have additional steps to perform.  
  
 In previous versions of BizTalk Server, all custom script included with a **Scripting** functoid was written inline. That is, when you created the functoid, all the script the functoid called during run time was stored with the functoid. If you wanted to use the same script with a different functoid, you either copied and pasted it from one **Scripting** functoid to another, or you rewrote the script from scratch.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copies existing inline scripts with the functoids when you migrate a map. However, not all of the scripts may function correctly. BizTalk Server uses Visual Basic .NET and JScript .NET rather than the VBScript and JScript used in previous versions. The .NET versions of the languages include some changes in syntax.  
  
> [!NOTE]
>  Be sure to test your **Scripting** functoids after migration.  
  
 You will need to rewrite custom functoids. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] expects custom functoids to use the .NET framework. It cannot use the older, COM-based custom functoids. Custom functoids can be rewritten to use the .NET framework. For sample code of a custom functoid, see [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md).  
  
 An alternative is to wrap the functionality of the custom functoid in an external assembly and call this assembly through a **Scripting** functoid. The following section describes this process.  
  
### To migrate your custom functoids  
  
1. Re-create the functionality of the functoid in a .NET language, such as Microsoft Visual Basic .NET, JScript .NET, or Microsoft Visual C# .NET.  
  
2. Create an assembly to contain the new functionality.  
  
3. Register the assembly in the global assembly cache (GAC).  
  
   > [!NOTE]
   >  To register assemblies in the global assembly cache, they must be strong named and signed. For more information about registering assemblies, see "Global Assembly Cache" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.  
  
4. Create a reference between the map that contains the **Scripting** functoid and the assembly that contains the rewritten functionality.  
  
5. Configure the **Script** property for the **Scripting** functoid. This property determines what script the **Scripting** functoid calls during run time. You must match the value of this property to the language into which you converted your custom script. For more information about how to configure the Script property, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md). Also see [Scripting Functoid](../core/scripting-functoid.md).  
  
6. Build the BizTalk project that contains the map with the **Scripting** functoid.  
  
7. Validate and test the map.  
  
## See Also  
 [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md)   
 [Scripting Functoid](../core/scripting-functoid.md)