---
title: "How to Add Existing Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fbeaea05-016e-488c-90f3-af8c6b9a3d84
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Existing Maps
There may be times when you want to add an existing map to a BizTalk project. Before doing so, you must ensure that the source and destination schemas of the map are included in the BizTalk project to which you are adding the map; or, referenced by the corresponding .NET assembly.  
  
### To add an existing map to a BizTalk project  
  
1. Right-click a BizTalk project in Solution Explorer, point to **Add**, and then click **Existing Item**.  
  
2. In the **Add Existing Item** dialog box, browse to the folder containing the map to be added, select it, and then click **Add**.  
  
    The map opens in BizTalk Mapper. The newly added map also appears as a child of the current BizTalk project in Solution Explorer.  
  
   > [!NOTE]
   >  If you browsed to a folder other than the BizTalk project folder, a copy of the map you added was created in the project folder, and it was this copy of the map that was added to the project. Subsequent changes to the map are made to this copy, not to the original map in the other folder.  
   > 
   > [!IMPORTANT]
   >  BizTalk maps can only be opened by BizTalk Mapper, which is hosted within the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell. If you double-click a map in Windows Explorer, a new instance of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] will be opened, and then the map will be opened by BizTalk Mapper, provided the corresponding schemas are loaded properly.  
   > 
   > [!NOTE]
   >  If the existing map contains custom functoids, then the corresponding DLLs must be copied to the folder “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”. Else, the map will not load and throws an error because of failure to load custom functoids.  
  
## See Also  
 [Managing Maps Within Projects](../core/managing-maps-within-projects.md)   
 [Developing Custom Functoids](../core/developing-custom-functoids.md)