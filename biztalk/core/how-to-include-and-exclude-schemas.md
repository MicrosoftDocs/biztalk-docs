---
title: "How to Include and Exclude Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9206458-e5d6-48d7-87a6-9471ba60dca7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Include and Exclude Schemas
A schema file can exist in a BizTalk project folder and not be included in that project. Such a schema is said to be excluded from the project. Excluded schemas are not compiled when you build the BizTalk project. This topic describes the steps required to include an excluded schema in a BizTalk project, and to exclude a schema from a BizTalk project.  
  
### To include a schema in a BizTalk project  
  
1.  In Solution Explorer, open the BizTalk project that contains the schema to be included in its project folder.  
  
2.  If all files are not already showing, on the **Project** menu, click **Show All Files**.  
  
3.  In Solution Explorer, right-click the excluded schema that you want to include, and then click **Include In Project**.  
  
     The icon for the previously excluded schema in Solution Explorer changes from an empty outline to the normal schema icon.  
  
4.  Optionally, on the **Project** menu, click **Show All Files** to hide all files in the project folder that are not included in the project.  
  
### To exclude a schema from a BizTalk project  
  
-   In Solution Explorer, right-click the schema that you want to exclude, and then click **Exclude From Project**.  
  
     The schema is now excluded from the BizTalk project.  
  
    > [!NOTE]
    >  When you exclude a schema from a project, the schema is not removed from the file system. However, the schema is not included when you build the project. You can choose whether or not to display excluded files in the project folder by toggling the **Show All Files** tool at the top of the Solution Explorer window.  
  
    > [!NOTE]
    >  If you want to delete the schema from the file system as well as removing the schema file from the project, you need to delete the schema. For more information about deleting schemas, see [Deleting Schemas](../core/how-to-delete-schemas.md).  
  
## See Also  
 [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)