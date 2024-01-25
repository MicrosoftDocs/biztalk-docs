---
description: "Learn more about: Retract"
title: "Retract"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Retract
You can use the **Retract** function to remove objects from the Business Rule Engine's working memory. The following paragraphs describe the behavior associated with retracting entities of different types from the rule engine's working memory.  
  
## .NET Objects  
 A .NET object is retracted in a policy by using the **Retract** function. This function is available in the Business Rule Composer as a **Functions** vocabulary item: drag the class (not the assembly or method) into the **Retract** parameter.  
  
> [!NOTE]
>  If you drag a method into the **Retract** function, the engine attempts to retract the object returned by the method.  
  
 Retracting a .NET object removes it from the rule engine's working memory and has the following impact:  
  
-   Rules that use the object in a predicate have their actions removed from the agenda (if any exist on the agenda).  
  
-   Actions on the agenda that use the objects are removed from the agenda.  
  
    > [!NOTE]
    >  Other actions higher up on the agenda may have already executed before the **Retract** function was called.  
  
-   The object is no longer evaluated by the engine.  
  
## TypedXmlDocument  
 You can either retract the original **TypedXmlDocument** that was asserted into the engine or retract one of the child **TypedXmlDocument**s created from a node of the parent **XmlDocument**.  
  
 Using the following XML as an example, you can either retract the **TypedXmlDocument** associated with order or one or both of the **TypedXmlDocument**s associated with orderline.  
  
```  
<order>  
   <orderline customer="Joe" linenumber="001">  
      <product name="router" quantity="10" cost="550" />  
   </orderline>  
   <orderline customer="Jane" linenumber="002">  
      <product name="switch" quantity="1" cost="300" />  
   </orderline>  
</order>  
```  
  
 To retract the order object, you would drag the top node for the schema in the XML Schemas fact pane. This node ends in ".xsd" and represents the document root node (not the document element node); it has a "/" selector that refers to the initial **TypedXmlDocument**. When the parent **TypedXmlDocument** is retracted, all **TypedXmlDocument** instances associated with the **TypedXmlDocument** (all **TypedXmlDocument**s created by calling the **Assert** function based on selectors used in the policy) are removed from working memory.  
  
 To retract only an individual child **TypedXmlDocument** (that is an orderline), you can drag this node from the XML Schemas pane into the **Retract** function. It is important to note that all **TypedXmlDocument**s are associated with the top-level **TypedXmlDocument** that was originally asserted, and not with the **TypedXmlDocument** that appears above it in the XML tree hierarchy. For example, product is a **TypedXmlDocument** below the orderline object; therefore, it would be associated with the order **TypedXmlDocument**, and not with the orderline **TypedXmlDocument**. In most instances, this distinction is not important. However, if you retract the order object, the orderline and product objects are also retracted. If you retract the orderline object, only that object is retracted, and not the product object.  
  
 The engine only works with and tracks object instances (**TypedXmlDocument**s) that it created when the **TypedXmlDocument** was initially asserted. If you create additional nodes—for example, sibling nodes to a node that was selected through a selector in the policy—these nodes are not evaluated in rules unless **TypedXmlDocument**s are created and asserted for them. Asserting these new, lower-level **TypedXmlDocuments** causes them to be evaluated in rules, but the top-level **TypedXmlDocument** does not have knowledge of them. When the top-level **TypedXmlDocument** is retracted, the new, independently asserted **TypedXmlDocument**s isl not automatically retracted. As a result, if new nodes are created, it is typically most straightforward to retract and reassert the full **XmlDocument**.  
  
 The **TypedXmlDocument** class supports a number of useful methods that can be called within a custom .NET member as part of an action. These include the ability to get the **XmlNode** associated with the **TypedXmlDocument** or the parent **TypedXmlDocument**.  
  
## TypedDataTable  
 You can retract either individual **TypedDataRow**s or the entire **TypedDataTable**. If you retract a table, all the containing rows are retracted from working memory.  
  
 To retract the entire **TypedDataTable** you need to use a helper function to access the **Parent** property on **TypedDataRow**, for example:  
  
```  
Retract(MyHelper.GetTypedDataTable(TypedDataRow))  
```  
  
 In the preceding action, you would drag the table into **TypedDataRow**. In **GetTypedDataTable** you would return the value of **TypedDataRow.Parent**.  
  
 As with **TypedXmlDocument**s, if you assert additional, new **TypedDataRow**s for the same **DataTable** after asserting the **TypedDataTable**, they are treated as individual entities and retracting the **TypedDataTable** does not result in the retraction of these extra **TypedDataRow**s. Only the **TypedDataRow**s contained in the **TypedDataTable** when it was asserted are retracted.  
  
## DataConnection  
 When a **DataConnection** is retracted, all **TypedDataRow**s retrieved from the database through the query constructed by the **DataConnection** are retracted from working memory. The **DataConnection** itself is also retracted, meaning that no more **TypedDataRow**s will be retrieved through the **DataConnection** (that is, through use of the **DataConnection** in other predicates or actions).  
  
 When using a **DataConnection**, any retract operation on an individual **TypedDataRow** puts the engine into an inconsistent state. Therefore, operations are not allowed on individual **TypedDataRow**s associated with a **DataConnection**. If you drag the table (using the **DataConnection** parameter) into the **Retract** function, you will be retracting the **DataConnection**.  
  
## See Also  
 [Engine Control Functions](../core/engine-control-functions.md)
