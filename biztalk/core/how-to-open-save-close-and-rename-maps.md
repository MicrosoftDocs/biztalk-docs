---
title: "How to Open, Save, Close, and Rename Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aa88ca7-a731-4295-8692-6dd36fdf0872
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Open, Save, Close, and Rename Maps
In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], maps exist as files in the file system with .btm extensions. Nevertheless, it is much more common to work with maps as items in a BizTalk project, from which you perform operations such as opening, saving, and closing maps.  
  
### To open a map  
  
1.  In Solution Explorer, select the map you want to open.  
  
2.  On the **View** menu, click **Open**.  
  
     The map opens in BizTalk Mapper.  
  
    > [!NOTE]
    >  You can also right-click the map in Solution Explorer, and then click **Open**, or simply double-click the map in Solution Explorer.  
  
### To save a map  
  
1. In Solution Explorer, select the map you want to save.  
  
2. On the **File** menu, click **Save *\<Name of Map\>***.  
  
### To save a map to a new location  
  
1.  In Solution Explorer, select the map you want to save to a new location.  
  
2.  On the **File** menu, click **Save *\<Name of Map\>* As**.  
  
3.  In the **Save File As** dialog box, browse to the folder location where you want to save the map.  
  
4.  In the **File name** box, type a name for the file, and then click **Save**.  
  
    > [!IMPORTANT]
    >  Do not use the following names for maps: "XmlContent", "SourceSchemas", "TargetSchemas", or "XsltArgumentListContent"; doing so will cause compilation problems in the generated C# code in the corresponding .NET assembly. For information about issues and their resolution, see [Troubleshooting Maps](../core/troubleshooting-maps.md).  
  
### To rename a map  
  
1.  In Solution Explorer, right-click the map that you want to rename, and then click **Rename**.  
  
2.  In the editing box that appears in the location of the map in Solution Explorer, type the new name for the map, or alter its existing name, and then press ENTER.  
  
> [!NOTE]
>  You may also want to change the **Type Name** of the map when you rename it. You change the **Type Name** by selecting the **map** in the solution explorer and entering the new name in the **Type Name** in the Properties window.  
  
#### To close a map  
  
1. In Solution Explorer, select the map you want to close.  
  
2. On the **File** menu, click **Close**.  
  
   > [!NOTE]
   >  You can also click the close icon ([**x**]) in the upper-right corner of the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.  
  
## See Also  
 [Managing Maps Within Projects](../core/managing-maps-within-projects.md)