---
title: "Extending Enumerations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enumeration values"
  - "2.X schemas, enumeration values"
ms.assetid: 043def35-b644-4502-a2e2-cc1a5fc0328a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Extending Enumerations
You can add values to the enumerations that establish accepted values for many fields, segments, and data types in HL7 message body, acknowledgment, and message body schemas. This involves changing the set of values in a specific table in the common table values schema file for the HL7 version in which you are working (the **Tablevalues_\<**<em>version</em>**\>.xsd** schema file).  
  
 You add to the enumeration in a different way for the message header schema than you do in other schemas, such as the message body schema. For the message header schema, you must change the table within the MSH_25_GLO_DEF.xsd file. For other schemas, you change the table in the table values schema file (tablevalues_\<version\>.xsd).  
  
### To add an enumeration value to the table values common schema file  
  
1. You first need to determine the table that contains the enumeration that you want to add to. In Solution Explorer of Visual Studio, open the schema file that contains the element that you want to change. In BizTalk Explorer, click the field element that you want to add a value for.  
  
   > [!NOTE]
   >  When you change an enumeration in the table values common schema file, all objects that reference that enumeration are affected.  
  
2. In the **Properties** pane, note the name of the table in the **Base Data Type** field.  
  
   > [!NOTE]
   >  If there is no table listed in **Base Data Type** field, and the **Derived By** property is not set to **Restricted**, then the field does not have an enumeration associated with it.  
  
3. In Solution Explorer, open the **Tablevalues_\<**<em>version</em>**\>.xsd**, and then click **Open**.  
  
   > [!NOTE]
   >  You must perform this procedure separately for each version of the HL7 schema that you want to change.  
  
4. In BizTalk Editor, browse to the table you want to change, and then click that table node.  
  
5. In the Properties window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.  
  
6. In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.  
  
### To add an enumeration value to a message header schema  
  
1. In Solution Explorer, open the MSH_25_GLO_DEF schema, and then click **Open**.  
  
2. Right-click the **MSH** node, point to **Insert Schema Node**, and then click **Child Field Element**. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] adds a field node to MSH, called **Field**. Click **ENTER**.  
  
3. In the **Properties** window, click the **Data Type** node, then from the drop-down list, select the table to which you want to add the enumeration value.  
  
4. In the **Properties** window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.  
  
5. In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.  
  
    When you add a value to the enumeration for any node, such as the **Field** node, you add that value globally for all objects that use that table. As a result, you can now delete the **Field** node, and the value will still be present for the table. You can verify this by scrolling in the right pane of BizTalk Editor to the table, and verifying that the value that you added is present.  
  
6. Right-click the **Field** node in BizTalk Editor, click **Delete**, and then click **Yes**.  
  
## See Also  
 [Table Values Common Schemas](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)   
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [Handling Undeclared Z Segments](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)