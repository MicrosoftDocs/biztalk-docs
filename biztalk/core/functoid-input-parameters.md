---
title: "Functoid Input Parameters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cca24f93-74a8-460c-b9ab-9aa2c767fe2f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---

# Functoid Input Parameters
A critical aspect of using functoids in your maps is properly configuring the input parameters to the functoid. While the order of input parameters is not critical for all functoids (such as the **Addition** functoid, which displays the same associate properties that one expects from addition), many functoids must have their input parameters specified in the correct order.  
  
## Create input paramaters
 There are two ways that input parameters to a functoid can be created:  
  
- By creating links into the left side of a functoid in the displayed grid page. The order in which you create the links is the order in which the associated input parameters are passed to the functoid.  
  
- By opening the **Configure \<Functoid\> Functoid** dialog box and adding new input parameters. This dialog box is also important because it allows you to reorder the input parameters to a functoid so that they are in the correct order. For example, if you create links to the functoid in the incorrect order, you can go to this dialog box and make the necessary corrections. For step-by-step instructions on configuring the input parameters for a functoid, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).  
  
  You must use the **Configure \<Functoid\> Functoid** dialog box to create input parameters that are constants.  
  
  When you provide a label for a link or functoid using the **Label** property in the Properties window when the link or functoid is selected, that label will be shown in the **Configure \<Functoid\> Functoid** dialog box rather than the corresponding XPath of a schema node, or the name of a functoid being used as an input parameter. With labels, it will be much easier to tell which parameter is which, and to get them into the correct order.  
  
  For definitive information about the correct order of functoid input parameters, see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## See Also  
 [Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md)   
 [Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)   
 [Configure the Table Looping and Table Extractor Functoids](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)