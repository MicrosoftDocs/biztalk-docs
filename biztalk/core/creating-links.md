---
description: "Learn more about: Creating Links"
title: "Creating Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maps, links"
  - "BizTalk Mapper, links"
ms.assetid: e8596c50-62e9-40a7-ad61-29cbdb4f4fc9
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Links
BizTalk Mapper helps you automate some elements involved in link creation. Simple link creation is similar to simple data types. There are more sophisticated forms of link creation that are more like structure assignment in a programming language. An example is a single link creation that specifies how multiple items of data are to be moved from input instance messages to corresponding output instance messages.  
  
 You create links using the following methods:  
  
-   **Simple link creation.** In simple link creation, you produce a link by dragging. Dragging a field in the source schema to a field in the destination schema causes the creation of an element or attribute in an output instance message and inserts the value of the element or attribute in the message. Such links can be made directly between **Record** and **Field** nodes in the source and destination schema, or they can include one or more functoids in a link path between **Record** and **Field** nodes in the source and destination schemas.  
  
-   **Structure links.** In creating structure links, you produce multiple simple links at the same time between **Record** and **Field** nodes in the source and destination schemas that have the same relative structure. To use structure linking, the structure of the relevant parts of the two schemas must be the same. For more information about configuring structure links, see [How to Link Records Automatically](../core/how-to-link-records-automatically.md).  
  
-   **Name-matching links.** When you use this method, you create multiple simple links at the same time between **Record** and **Field** nodes in the source and destination schemas based on the names of the **Records** and **Field** nodes. To use name-matching linking, the structure of the source and destination schemas must be very similar, but not exactly the same. For more information about configuring name-matching links, see [How to Link Records Automatically](../core/how-to-link-records-automatically.md).  
  
    > [!NOTE]
    >  You can also see [How to Manage Existing Links](../core/how-to-manage-existing-links.md) for information about how to change/modify the existing links.  
  
## Preserving Whitespace in a Link  
 If you want to preserve whitespace from a source element when mapping to a target element or functoid, you will need to write a custom script.  
  
 Whitespace is not preserved either in the Mapper or in the runtime system. Both the Mapper and the runtime system use BTSXslTransform.Transform which handles large-message transformations and relies on XmlReader to navigate using the XPath data model.  
  
 To preserve whitespace, you can write a custom script that returns the required amount of whitespace. For example, the code below always returns a string containing 5 whitespace characters:  
  
```  
public string Whitespace(string param1)  
{  
  return "     ";  
}  
```  
  
 If you link a source element to the input of this script and a target element as the output, when the map is executed, the output element will contain 5 whitespace characters.  
  
> [!NOTE]
>  If you view the output using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the element will appear empty. This is because the XML viewer treats elements containing whitespace only as empty. To see the whitespace, right-click the XML view and select **View Source**.  
  
## See Also  
 [How to Edit Link Properties](../core/how-to-edit-link-properties.md)
