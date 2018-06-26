---
title: "How to Save, Rename, and Close Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65e15d9e-40ae-4850-9c13-88033cb3b3bb
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Save, Rename, and Close Schemas
In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], schemas are XML Schema definition (XSD) language files and reside on the file system with .xsd extensions. When you use BizTalk Editor to develop schemas, you will routinely need to save and close schema files, and occasionally you may need to rename them. This topic describes the steps required to perform these basic operations.  
  
### To save a schema  
  
1. If necessary, activate BizTalk Editor for the schema to be saved by clicking the appropriate tab at the top of the main editing window in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. On the **File** menu, click **Save *\<Name of Schema\>***.  
  
    If the schema had unsaved changes, its name as displayed on the tab at the top of the main editing window will no longer end with an asterisk (*), which is used to indicate unsaved changes.  
  
> [!NOTE]
>  You can save the schema under a new name by clicking **Save *\<Name of Schema\>* As** on the **File** menu.  
  
> [!NOTE]
>  You can save the schema as part of saving all changed items in the project by clicking **Save All** on the **File** menu.  
  
#### To rename a schema  
  
1.  In Solution Explorer, right-click the schema that you want to rename, and then click **Rename**.  
  
2.  In the editing box that appears in the location of the schema in Solution Explorer, type the new name for the schema, or alter its existing name, and then press ENTER.  
  
> [!NOTE]
>  You may also want to change the **Type Name** of the schema when you rename. You change the **Type Name** by selecting the **schema** in the solution explorer and entering the new name in the **Type Name** in the Properties window.  
  
> [!IMPORTANT]
>  You should not rename any schema that is being used by another schema. This includes schemas that have been included, imported, or redefined by other schemas, as well as property schemas for which promotions have already been established. If you do so, the schema that is being used will not be able to find the renamed schema because the name it contains will no longer be accurate.  
  
> [!NOTE]
>  Certain name choices for project member files, such as schema files, can cause compilation errors later on due to conflicts with C# reserved words and.NET Framework type and namespace names (such as "System"). Examples for schemas include schema.xsd, XmlContent, and RootNodes. This is because the **Type Name** property defaults to the base (non-extension) portion of the **Filename** property. You can work around this type of compilation error by explicitly changing the value of the **Type Name** property to something that does not conflict.  
  
#### To close a schema  
  
1. If necessary, activate BizTalk Editor for the schema to be closed by clicking the appropriate tab at the top of the main editing window in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. On the **File** menu, click **Close**.  
  
    BizTalk Editor closes for the schema that has been closed.  
  
## See Also  
 [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)