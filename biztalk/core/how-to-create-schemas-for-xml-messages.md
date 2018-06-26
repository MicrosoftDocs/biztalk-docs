---
title: "How to Create Schemas for XML Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0270293-fe23-42bd-b090-e877d5e9ce0b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Schemas for XML Messages
There are several methods for creating BizTalk message schemas. This topic provides step-by-step instructions for some of those methods.  
  
### To create a new schema  
  
1. In **Solution Explorer**, select the BizTalk project to which you want to add a schema.  
  
2. On the **Project** menu, click **Add New Item**.  
  
3. In the **Add New Item - \<*BizTalk ProjectName*\>** dialog box, in the **Templates** section, click **Schema**.  
  
4. In the **Name** box, type a name for the schema, and then click **Add**.  
  
5. If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.  
  
6. In the schema tree view, select the **Schema** node, and then in the Properties window, select the **Target Namespace** property and type a name for the target namespace. It is important that you set this property in this initial phase of schema creation; avoid using the default **Target Namespace** property value.  
  
   > [!NOTE]
   >  Certain name choices for project member files, such as schema files, can cause compilation errors later on due to conflicts with C# reserved words and.NET Framework type and namespace names (such as System). Examples for schemas include schema.xsd, XmlContent, and RootNodes. This is because the **Type Name** property defaults to the base (non-extension) portion of the  **Filename** property. You can work around this type of compilation error by explicitly changing the value of the **Type Name** property to something that does not conflict.  
  
   > [!NOTE]
   >  You may need to add, delete, and modify the records and fields in your schema along with their associated properties. To learn more about this, see [Managing the Nodes Within a Schema](../core/managing-the-nodes-within-a-schema.md).  
  
### To generate a schema from a non-XSD source  
  
1.  In **Solution Explorer**, right-click a BizTalk project, point to **Add**, and then click **Add Generated Items**.  
  
2.  In the **Add Generated Items - \<*BizTalk ProjectName*\>** dialog box, in the **Templates** section, click **Generate Schemas**, and then click **Add**.  
  
3.  In the **Generate Schemas** dialog box, in the **Document type** drop-down list, select **XDR Schema**, **DTD Schema**, or **Well-Formed XML**.  
  
     If you see either **DTD (Not Loaded)** or **Well-Formed XML (Not Loaded)** in the drop-down list, select the appropriate document type anyway, and you will be guided through the process of installing the missing DLL. Then repeat these steps.  
  
4.  In the **Generate Schemas** dialog box, click **Browse**, locate the file you want to import, and then click **Open**. The file you locate must match the document type you selected in the previous step.  
  
     A new schema is generated from the specified file, using the same name as that file with the .xsd extension, and opened in BizTalk Editor.  
  
## See Also  
 [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)