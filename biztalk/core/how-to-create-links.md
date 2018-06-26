---
title: "How to Create Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 670b831f-be03-4612-93d5-a894f7bb3c11
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Links
Creating a link from a **Record** or **Field** node in a source schema to a **Record** or **Field** node in a destination schema is the most basic activity in creating maps. This topic provides step-by-step instructions for several variations of this activity, including creating links to and from functoids. For additional information about working with functoids, see [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md).  
  
 The instructions in this topic assume you already have a BizTalk map open, and that you have chosen source and destination schemas for the map. For more information about opening maps and choosing schemas for the map, see [Managing Maps Within Projects](../core/managing-maps-within-projects.md).  
  
### To create links between Field and Record nodes  
  
1. In BizTalk Mapper, drag a **Field** or **Record** node from the source schema tree to a **Field** or **Record** node in the destination schema tree.  
  
    **- Or -**  
  
2. In BizTalk Mapper, drag a **Field** or **Record** node from the destination schema tree to a **Field** or **Record** node in the source schema tree.  
  
   There are several things to consider when creating links:  
  
-   The data type of a **Field** or **Record** node in the source schema tree should match the data type of a **Field** or **Record** node to which it is linked in the destination schema tree.  
  
-   If a **Field** or **Record** node in the source schema is optional, and a particular source instance message does not contain the corresponding element or attribute, BizTalk Mapper will not create a corresponding element or attribute in the destination instance message, even if the **Field** or **Record** nodes have a direct link between them in the map.  
  
-   You cannot link to a **Field** or **Record** node in the destination schema that has a constant value associated with it. On the other hand, you can link to a required **Field** or **Record** node in the destination schema that has a default value associated with it. Note, however, that when you test the map, the default value will be used.  
  
-   You cannot create a link to or from the **Any Element**, **Any Attribute**, **Sequence Group**, or **Choice Group** nodes. For more information about these types of nodes, see the following topics, see [Any Element Nodes](../core/any-element-nodes.md), [Sequence Group Nodes](../core/sequence-group-nodes.md) or [Choice Group Nodes](../core/choice-group-nodes.md).  
  
-   You may need to expand the schema trees to view the fields that you want to map. For more information, see [How to Expand and Collapse the Schema Trees](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx).  
  
#### To create links between Record or Field nodes and functoids  
  
1.  In BizTalk Mapper, drag a **Record** or **Field** node from the source or destination schema to a functoid in a grid page.  
  
     **- Or -**  
  
2.  Drag the functoid from a grid page to a **Record** or **Field** node in the source or destination schema.  
  
     When you create a link between a **Record** or **Field** node in the source schema and a functoid, you are creating an input to that functoid. When you create a link between a **Record** or **Field** node in the destination schema and a functoid, you are creating an output from that functoid.  
  
    > [!IMPORTANT]
    >  You cannot link between a functoid and an **Any Element** node or an **Any Attribute** node.  
  
    > [!NOTE]
    >  You must first add a functoid to a grid page before you can add a link between a **Record** or **Field** node and that functoid. For more information about adding functoids to a grid page, see [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md). Also see [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md).  
  
    > [!NOTE]
    >  You cannot link to a **Field** node in the destination schema that has a constant value associated with it. On the other hand, you can link to a required **Field** node in the destination schema that has a default value associated with it. Note, however, that when you test the map, the default value will be used.  
  
#### To create links between functoids  
  
-   In BizTalk Mapper, drag one functoid to another functoid in a grid page.  
  
    > [!NOTE]
    >  Links are processed left-to-right in a grid page. You cannot make a link from one functoid to another functoid directly above or below it. Links between functoids are interpreted such that a link signifies output from the functoid to the left and input to the functoid to the right.  
  
### To change the endpoint of a link  
 In a map, you can drag an endpoint of a link and drop it over another node or functoid.  
  
 To change the endpoint of a link:  
  
1. Click the link for which you want to change the source or destination node/functoid. The endpoints of the link become bold.  
  
2. Hold down the mouse key on any of the bold endpoints and drag the link to the desired node/functoid. This changes the linking from the previous node/functoid to the new node/functoid.  
  
   However, you cannot perform this operation for invalid linking, such as:  
  
-   Adding a link as an input to Date/Time functoids. The Date/Time functoids do not need any input links.  
  
-   Duplicating links from intermediate functoids.  
  
     If you link Node1 to Node2, and also from Node1 to Node3, you cannot drag the endpoint of the link at Node2 to change and link to Node3.  
  
## See Also  
 [Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md)