---
title: "How to Create Schemas That Use Other Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff0bcd9a-6c66-4c3b-bd41-64047a7c8392
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Schemas That Use Other Schemas
XML Schema definition (XSD) language provides three different but related mechanisms for using one schema within another schema. These mechanisms are importing a schema, including a schema, and redefining a schema. For a brief summary of these mechanisms and how they differ, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md). For detailed information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md) for links to the XSD primer and specifications.  
  
 This topic describes the steps required to import, include, and redefine other schemas within the schema you are developing.  
  
### To import, include, or redefine one schema within another schema  
  
1. In BizTalk Editor, open the schema to which you want to import, include, or redefine another schema. You can open a schema by double-clicking it in Solution Explorer.  
  
2. Select the **Schema** node at the top of the schema tree view.  
  
3. If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.  
  
4. In the Properties window, in the **Advanced** category, in the value portion of the **Imports** property, click the ellipsis (**...**) button.  
  
5. In the **Imports** dialog box, in the **Import New Schema as** list, select **XSD Import**, **XSD Include**, or **XSD Redefine**, as appropriate, and then click **Add**.  
  
6. In the **BizTalk Type Picker** dialog box, expand the **Schema** node in the project tree, select the schema that you want to import, include, or redefine, and then click **OK**.  
  
7. In the **Imports** dialog box, click **OK**.  
  
    The appropriate XSD directives to implement the import, include, or redefine operation are added to the **schema** element in the XSD view, including a new **import**, **include**, or **redefine** element, as appropriate.  
  
> [!IMPORTANT]
>  Make sure you understand the different purposes of these three mechanisms, such as how they differ with respect to namespace requirements. You can always delete a previously imported, included, or redefined schema and then use one of the other two mechanisms, but depending on how extensively you have referenced that schema, you may need to rework your schema accordingly.  
  
> [!IMPORTANT]
>  The XSD mechanism for importing, including, and redefining one schema within another schema works by reference to the imported, included, or redefined schema. This means that if you make a change to the imported, included, or redefined schema, that change will be reflected in the schema containing the import, include, or redefine reference.  
  
## See Also  
 [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)   
 [How to Create References to Another Node or Type](../core/how-to-create-references-to-another-node-or-type.md)