---
description: "Learn more about: How to Create Property Schemas"
title: "How to Create Property Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Create Property Schemas
If you choose to promote fields as property fields, you will need to define a property schema first. This property schema specifies an unstructured collection of fields into which you can promote fields from within an instance message defined by a schema associated with your property schema.  
  
> [!IMPORTANT]
>  Do not copy and edit an existing property schema to create a new schema. The property schema contains schema-specific internal data.  
  
> [!NOTE]
>  You do not need to create a property schema to promote distinguished fields.  
  
### To create a property schema  
  
1.  In **Solution Explorer**, right-click a BizTalk project, point to **Add**, and then click **New Item**.  
  
2.  In the **Add New Item** dialog box, in the **Templates** section, click **Property Schema**.  
  
3.  In the **Name** box, type a name for the schema, and then click **Add**.  
  
     The new property schema opens, and it already contains a **Field Element** node named Property1.  
  
4.  In the schema tree, right-click that **Field Element** node, click **Rename**, type a descriptive name for the first property in the schema, and then press ENTER.  
  
5.  Set the **Data Type** and other relevant properties, as appropriate, for the **Field Element** node in the Properties window.  
  
6.  If you want to insert **Field Element** nodes for additional properties, right-click the \<Schema\> node, click **Insert Schema Node**, and then click **Child Field Element**, and then repeat steps 4 and 5. Repeat as necessary to create the required set of **Field Element** nodes into which you intend to promote values from instance messages.  
  
## See Also  
 [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)
