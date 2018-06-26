---
title: "How to Set Node Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0c79eac-d9ba-45e2-a6e9-770b2bcb2067
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set Node Properties
After inserting a node into a BizTalk schema, you will often need to change the properties of that node from their default values. Each type of node has a distinct set of properties, and within one of those sets, the settings of one property can affect the availability of other properties. For example, before setting the **Default Wrap Character** property of the **Schema** node, you must set the **Default Wrap Character Type** property to either **Character** or **Hexadecimal**, thereby establishing the format in which you intend to represent the former property. Further, neither of these properties is available, nor is the entire **Parse** property category to which they belong, unless **Flat File Extension** is enabled by using the **Schema Editor Extensions** property.  

 Node properties are extensive and can be complex, as is the XML Schema definition (XSD) language that they support. This topic only briefly describes the general steps involved in examining and setting node properties. For detailed information about these properties, including, for example, information about their default and allowed values, see the **Schema Property Reference**. For even more detailed information about the XSD concepts and elements that underlie most of these node properties, refer directly to information about [XSD on the Web](../core/xsd-resources-on-the-web.md).  

More info on these properties, and the schema property reference [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

  
## Examine a node property value  
  
1. In BizTalk Editor, open the schema that contains the property you want to examine, and then select the node that contains that property.  
  
2. If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.  
  
3. If necessary, scroll the Properties window to find the property of interest, and note its value.  
  
    You can use buttons at the top of the Properties window to change the way that the properties are sorted, either alphabetically within their categories, or alphabetically without regard for (or display of) their categories.  
  
## Set a node property value  
  
1. In BizTalk Editor, open the schema that contains the property you want to set, and then select the node that contains that property.  
  
2. If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.  
  
3. If necessary, scroll the Properties window to find the property of interest.  
  
    You can use buttons at the top of the Properties window to change the way that the properties are sorted, either alphabetically within their categories, or alphabetically without regard for (or display of) their categories.  
  
4. Set the value of the property in the value field, which is to the right of the property name. Depending on the type of the property, you might type a value or choose a value from the drop-down list that is displayed when the value field is selected. Some properties allow either operation. Some properties display an ellipsis (**...**) button that when clicked opens a dialog box in which more complicated values, such as collections, can be set.  
  
5. If you have typed a new value for the property, finish by pressing ENTER.  
  
##  Clear a node property value  
  
1.  Select the node that contains the property of interest.  
  
2.  In the Properties window, double-click the property value that you want to clear, right-click the property value, and then click **Delete**.  
  
## Restore a node property to its default value  
  
1.  Select the node that contains the property of interest.  
  
2.  In the Properties window, right-click the property name that you want to reset to its default value, and then click **Reset**.  
  
## See Also  
 [Working with Existing Nodes](../core/working-with-existing-nodes.md)