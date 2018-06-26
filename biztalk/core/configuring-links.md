---
title: "Configuring Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10050c28-0944-4073-afd2-54cd6c8d79a2
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Links

## Overview
Links have properties that are displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when a link is selected in the displayed grid page. For reference information about the properties associated with links, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 

## Source, target and label  
 The following properties configure links in a map:  
  
- **Source Links**. You use the **Source Links** property to configure the nature of the data from an input instance message that will be used to construct the output instance message. The default, and most common choice, is to use the element or attribute value from the input instance message. Other choices are possible, including the use of the name of the element or attribute from the input instance message. For more information about this property and its available choices, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
- **Target Links**. You use the **Target Links** property to configure how BizTalk Mapper will match node-hierarchy levels. By default, source schema hierarchies are flattened as the output instance message is created. You can also choose to have hierarchies preserved, matching links from either the top down or from the bottom up. For more information about this property and its available choices, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
- **Label**. You use the **Label** property to create a more readable name for the link than the XPath value that is used by default. Configuring this property is especially helpful when the link is used as an input for table-driven looping. For more information about this property and its available choices, and about table-driven looping, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. Also see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md), respectively.  
  
## See Also  
  [How to Edit Link Properties](../core/how-to-edit-link-properties.md)