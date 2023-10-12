---
description: "Learn more about: How to Migrate XDR Schemas to XSD Schemas"
title: "How to Migrate XDR Schemas to XSD Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Migrate XDR Schemas to XSD Schemas
If you are migrating schemas from a previous version of BizTalk Server, you will need to convert your XML-Data Reduced (XDR) schemas into XML Schema definition (XSD) language schemas. This topic describes the necessary steps.  
  
### To generate an XSD schema from an XDR schema  
  
1.  In **Solution Explorer**, right-click the relevant BizTalk project, point to **Add**, and then click **Add Generated Items**.  
  
2.  In the **Add Generated Item - \<*BizTalk ProjectName*\>** dialog box, in the **Templates** section, click **Generate Schemas**, and then click **Add**.  
  
3.  In the **Generate Schemas** dialog box, in the **Document type** list, select **XDR Schema**.  
  
4.  Click **Browse**, locate the XDR schema file you want to migrate, and then click **OK**.  
  
     A new schema is generated from the specified XDR schema file, using the same name as that file with the .xsd extension, and then opened in BizTalk Editor.  
  
> [!NOTE]
>  Avoid using C# reserved words and .NET Framework type and namespace names (such as System) as schema root node names or as file names.  
  
## See Also  
 [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)   
 [Migrating Flat File Records](../core/migrating-flat-file-records.md)
