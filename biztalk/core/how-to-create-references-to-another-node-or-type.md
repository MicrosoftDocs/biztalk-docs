---
title: "How to Create References to Another Node or Type | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c60be9ad-01a9-40e7-b43b-8c3d09bbb32f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create References to Another Node or Type
You can use global nodes to create reusable data types—fragments of structure—that you can use throughout the schema wherever that structure is appropriate. You can only use nodes that are direct children of the **Schema** node to create global types.  
  
 You can also create cyclical references using the data types of nodes that are not direct descendants of the **Schema** node. This is useful for representing recursive structures in schemas.  
  
 This topic provides step-by-step instructions for various types of global nodes and how to refer to them to use them.  
  
 **Creating Global Declarations**  
  
 You can create global types using records, fields or attributes. Global types created from records may only be used in records, types created from fields only in fields, attribute types only in attributes. The following procedures describe how to define and use global declarations.  
  
## Create a global declaration from a node  
  
1.  Select the **Record** , **Field Attribute**,or **Field Element** node whose type you want to make globally available.  
  
2.  In the **Properties** window, type a name in the **Data Structure Type** list that will be used as the global name for the complex type, and then press ENTER.  
  
## Create a globally defined Sequence Group node, Choice Group node, or All Group node  
  
1.  Select the **Record** node into which you want to insert the globally defined group node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sequence Group**, **Choice Group**, or **All Group**, as appropriate.  
  
3.  Create a structure in the newly inserted group. For example, insert **Record** or **Field Element** nodes to express the structure of the data within the group node.  
  
    > [!NOTE]
    >  Sequence Group, **Choice Group**, and **All Group** nodes can only contain nodes that correspond to XML elements and therefore cannot contain **Field Attribute** nodes.  
  
4.  Select the group node inserted in step 2.  
  
5.  In the Properties window, click **Group Reference**, type a name into the value field, and then press ENTER.  
  
     By providing a name in the **Group Reference** property, you have globally defined group node, after which you can associate other group nodes with this globally defined type (structure).  
  
## Create a globally defined Attribute Group node  
  
1.  Select the **Record** node into which you want to insert the globally defined **Attribute Group** node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Attribute Group**.  
  
     This adds an **Attribute Group** node to the end of the child nodes in the selected **Record** node.  
  
3.  Add the appropriate **Field Attribute** or **Attribute Group** nodes to your **Attribute Group**.  
  
4.  Optionally, if you want to rename the **Attribute Group** node, select the **Attribute Group** node and change its **Group Reference** property to a new name of your choosing.  
  
     Attribute groups are always global and referenced from their point of use.  
  
## Use a type or group that has been globally defined  
  
1. Select the node for which you want to use a globally defined type.  
  
2. In the Properties window, select the globally defined type from the drop-down list for the **Data Structure Type** property (**Record** nodes), **Data Type** property (**Field Element** and **Field Attribute** nodes), or **Group Reference** (**Sequence Group**, **Choice Group**, **All Group**, and **Attribute Group** nodes). More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
   > [!NOTE]
   >  Subsequent changes to the globally defined type or group can be made in any of the schema locations in which it appears. These changes will be applied in all such locations as you make them in the single, arbitrary location.  
  
   After you have created a global declaration, you cannot delete it in a single step. However, you can delete it by using the **Cleanup Global DataTypes** dialog box when the schema is saved, using the following procedure.  
  
## Delete a global declaration  
  
1.  Delete all of the nodes where this global type or group is used, or specify a different type or group to be used in all of those nodes, or some combination thereof. For step-by-step instructions for deleting a node, see [Deleting Nodes](../core/how-to-delete-nodes.md).  
  
2.  Upon saving your specification, the **Cleanup Global DataTypes** dialog box appears. Select the global declaration you want to completely delete from your specification, and then click **OK**.  
  
    > [!NOTE]
    >  The **Cleanup Global DataTypes** dialog box appears every time you save a schema with unused data types. If this dialog box does not appear, either all data types are used somewhere in the schema or the schema has not been modified since it was opened (in the latter case, it might still contain unused data types that were previously retained.  
  
## Create Cyclical References to Another Node  
 You can create cyclical references to a node to represent recursive schema elements. You do this by creating a node whose type is defined by an enclosing record. For example, consider an instance message that is wrapped in an arbitrary number of envelopes having the same structure. Using cyclical references, you can create a schema that defines such instance messages.  
  
### Create a cyclical reference  
  
1.  Select a **Record** node for which you want to create a recursive reference. This is the node representing the top of the recursive structure.  
  
2.  In the Properties window, verify that the **Data Structure Type** has a value.  
  
     Verifying that the **Record** node has a named type associated with it is necessary because recursive structures are defined when a type contains itself. Types can only contain themselves through nested use of named global types.  
  
3.  Select a child **Record** node or insert a child **Record** node.  
  
4.  For the child **Record** node, in the Properties window, in the **Data Structure Type** list, select the data structure identified in step 2.  
  
> [!IMPORTANT]
>  - The **Min Occurs** property for the repeating node must be set to zero (**0**). Setting it to one (**1**) causes an infinite loop.  
>
>  - If you import a schema that contains a recursive element, BizTalk Editor does not automatically check to ensure that the recursive element is valid.  
  
## See Also  
 [Managing the Nodes Within a Schema](../core/managing-the-nodes-within-a-schema.md)