---
title: "Creating Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc9f8ad1-4aad-4866-8aa4-4877fdc5e5f9
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Maps
The primary user interface for BizTalk Mapper is displayed on a tab within the [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window. This display is divided into three panes. The left pane displays the source schema as a tree. The right pane displays the destination schema as a tree. The middle pane displays the grid as multiple pages. To indicate how you want to map data from the source schema to the destination schema, you draw lines between the records and fields you want to map. These lines are called *links*, and they are the most basic way to specify the mapping of data. For more information about linking records and fields, see [Links in Maps](../core/links-in-maps.md).  
  
 If you want to implement more advanced mapping methods, you can use functoids. Functoids are tools available on BizTalk Mapper tabs within the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox. They enable you to create maps to perform more complex operations, such as:  
  
- Adding the values in two fields in a source schema and putting the result in a field in the destination schema.  
  
- Calculating the average value of a field in a looping record and putting the result in a field in the destination schema.  
  
- Writing a custom script to manipulate instance data as appropriate for your business needs.  
  
  For more information about functoids, see [Functoids in Maps](../core/functoids-in-maps.md).  
  
  BizTalk Mapper can support many different mapping scenarios from simple parent-child relationships to detailed, complex looping of records and hierarchies. Consider the following when you create maps:  
  
- BizTalk Mapper does not support merge and sort.  
  
- If the source and target schema structures are extremely different, it is possible that the transformation cannot be done in a single map. You may need a double pass.  
  
- **Looping** functoids are flexible and powerful, yet you will not be able to break up the iteration when a change in value on the source schema is detected to start the next iteration of the target loop.  
  
- You can declare a variable outside the method in a **Scripting** functoid, which results in the variable being in scope for the life of the map. Therefore, you can use the **Scripting** functoid for holding values between scope areas of the transformation.  
  
  All data processed by [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] at run time must be in XML format. All non-XML data must be translated to an equivalent XML format before mapping. Similarly, when the mapping process is complete, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the output of a mapping operation to create a file format that is recognized by the trading partner or application to which the data is sent.  
  
  BizTalk Mapper includes a compiler. This tool-level component generates the Extensible Stylesheet Language Transformations (XSLT) needed to transform or translate input instance messages to output instance messages.  
  
  This section provides task-specific information about using BizTalk Mapper to create the mapping between two schemas. It assumes that you already have BizTalk Mapper open, and have chosen your source and destination schemas.  
  
## In This Section  
  
-   [Managing Maps Within Projects](../core/managing-maps-within-projects.md)  
  
-   [Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md)  
  
-   [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md)  
  
-   [How to Create a Map without Maps](../core/how-to-create-a-map-without-maps.md)  
  
-   [Managing Default Mapper Behavior Using \<mapsource\>](../core/managing-default-mapper-behavior-using-mapsource.md)