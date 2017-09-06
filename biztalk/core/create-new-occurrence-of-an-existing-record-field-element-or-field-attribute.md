---
title: "How to Create a New Occurrence of an Existing Record, Field Element, or Field Attribute Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02380f68-056c-47c4-a0d6-61d599a4685d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a New Occurrence of an Existing Record, Field Element, or Field Attribute Node
You can create new instances of an existing **Record**, **Field Element**, or **Field Attribute** node such that subsequent modifications to any instance are reflected in all instances.  
  
### To create a new instance of an existing Record, Field Element, or Field Attribute node  
  
1.  Select the original **Record**, **Field Element**, or **Field Attribute** node, make sure its **Base Data Type** property is set correctly, and then in its **Data Structure Type** (**Record** nodes) or its **Data Type** (**Field Element** and **Field Attribute** nodes) property, type a custom data type name.  
  
2.  Insert the new **Record**, **Field Element**, or **Field Attribute** node and set one of the following properties to the custom data type name you typed in step 1.  
  
    -   Data Structure Type (**Record** nodes)  
  
    -   Data Type (**Field Element** and **Field Attribute** nodes)  
  
    > [!NOTE]
    >  If a new **Record** or **Field Element** node is a sibling of the original node, and you give the new node the same name as the original node, you will see a message box asking about duplicate nodes in the same scope with the same name. Clicking **Yes** performs the same action as choosing the custom data type name in step 2.  
  
> [!NOTE]
>  You have created a new instance of the existing **Record**, **Field Element**, or **Field Attribute** node.  
  
> [!NOTE]
>  Some properties of **Record**, **Field Element**, or **Field Attribute** node instances remain identical (a change to one instance is a change to all instances), and other properties can be set independently for each instance.  
  
## See Also  
 [Inserting Nodes into a Schema](../core/inserting-nodes-into-a-schema.md)