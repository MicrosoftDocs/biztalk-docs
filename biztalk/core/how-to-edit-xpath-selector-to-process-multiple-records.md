---
title: "How to Edit XPath Selector to Process Multiple Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Rules Framework, editing multiple records"
  - "Business Rules Framework, code samples"
  - "Business Rules Framework, programming"
ms.assetid: ef7e1f8d-2e29-4cef-b558-0090648bffc0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Edit XPath Selector to Process Multiple Records
Separate child TypedXmlDocuments are created when a TypedXmlDocument is asserted into the engine; see [Assert](../core/assert.md). The engine determines which child TypedXmlDocuments to create based on the XPath selectors defined in the rules. When you build rules in the Composer, the XPath Selector value defaults to the node above the node selected in the XML Schemas tab in the Facts Explorer. The XPath Field value defaults to the selected node itself, relative to its parent node.  
  
 In some situations you may want to customize the default XPath that the Composer creates when building rules. Assume the following sample XML document.  
  
```  
<Order>  
   <Orderline>  
      <Hat style="Baseball">                        
         <Cost>10</Cost>  
      </Hat>  
      <Shirt color="Black">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
   <Orderline>  
      <Hat style="Bowler">                        
         <Cost>20</Cost>  
      </Hat>  
      <Shirt color="Red">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
</Order>  
```  
  
 Assume that you want to build a rule that calculates the Total value for each Orderline. Your rule would look like the following.  
  
 IF 1==1  
  
 THEN <strong>/Order/Orderline/</strong>Total = (<strong>/Order/Orderline/Hat/</strong>Cost + <strong>/Order/Orderline/Shirt/</strong>Cost)  
  
 The bold portion of the XPaths indicate the Selector portion and the remainder represents the Field XPath. These are the defaults built by the Composer. Running this policy, however, would result in the creation of 6 objects—2 Orderline objects, 2 Hat objects, and 2 Shirt objects. The Orderline totals would be calculated for each combination of Hat and Shirt objects and the totals would always be set to the same value, which resulted from the last execution of the rule. The rule would fire 8 times. This is not what is intended in this scenario.  
  
 One solution would be to edit the XPath values to be as follows.  
  
 IF 1==1  
  
 THEN <strong>/Order/Orderline/</strong>Total = (<strong>/Order/Orderline/</strong>Hat/Cost + <strong>/Order/Orderline/</strong>Shirt/Cost)  
  
 The Selector XPath values for all three fields have been set to the same /Order/Orderline value and the Field XPath values have been edited accordingly. This is done by changing the XPath Selector and XPath Field values in the Properties window when a node is selected in the XML Schemas tab. This should be done prior to dragging the field into a rule argument.  
  
 Executing the policy with this change would result in the Total value being correctly calculated for each Orderline based on the Cost values of the Shirt and Hat nodes within that Orderline.