---
description: "Learn more about: Data Transformation Configuration"
title: "Data Transformation Configuration"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Transformation Configuration
When mapping from an element, a typical Extensible Stylesheet Language Transformations (XSLT) looks as follows.  
  
```  
<xsl:attribute name='CatalogPurposeCode'>  
     <xsl:value-of select='BCT/BCT01/text()'/>  
</xsl:attribute>  
```  
  
 If the element **BCT01** contains mixed content, the use of text() makes it possible to access the first text only up to the point of the first subelement, if any. If text() were not used in this XSLT statement, the result would be that all text content, plus any text content of subelements, would be mapped as one string of text. Configuring the **Source Links** property for a link allows you to control the source of the data that is copied into the structure defined by the destination schema.  
  
 When you select a link in the displayed grid page, one of the properties displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window is the **Source Links** property. You can choose between the following possible values for each link in your map:  
  
-   **Copy text value.** Use this value, which is the default, to copy the value of the element or attribute in the input instance message. For example, if the relevant element is BoldExample, as follows:  
  
    ```  
    <BoldExample>This is a <B>Bold Text</B> example.</BoldExample>  
    ```  
  
     The value copied into the relevant element or attribute in the output instance message is "This is a ". For mixed content elements like this, this result may not be what is desired. But because mixed content elements are relatively rare, the **Copy text value** setting for the **Source Links** property is probably appropriate in most cases.  
  
-   **Copy name.** Use this value to copy the name of the node in the input instance message. For the example in the **Copy text value** description, the result is "BoldExample", which is the actual name of the element.  
  
-   **Copy text and sub content value.** Use this value to concatenate the values of the node and all values of its child nodes in the input instance message. For the example in the **Copy text value** description, the result is "This is a Bold Text example.", which might very well be the appropriate result for elements defined to contain mixed content.  
  
## See Also  
 [Mass Copy Functoid](../core/mass-copy-functoid.md)   
 [How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md)   
 [Node-Hierarchy Level Matching](../core/node-hierarchy-level-matching.md)
