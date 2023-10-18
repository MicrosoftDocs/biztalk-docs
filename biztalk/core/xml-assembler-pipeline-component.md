---
description: "Learn more about: XML Assembler Pipeline Component"
title: "XML Assembler Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# XML Assembler Pipeline Component
The XML Assembler pipeline component combines XML serializing and assembling in one component. Its primary function is to transfer properties from the message context back into envelopes and documents.  
  
 The following actions occur in the XML Assembler component after receiving a batch of messages to form an interchange:  
  
1.  The assembler creates the envelope by using the specified envelope specification.  
  
2.  The component puts the content properties on the message instances by using the predefined XPaths coded as annotations in the XSD schemas associated with the message.  
  
3.  The component appends the message to the envelope.  
  
4.  The component puts the content properties on the envelope by using the predefined XPaths coded as annotations in the XSD schemas associated with envelopes.  
  
> [!NOTE]
>  The XML Assembler pipeline component does not populate missing attribute fields, but does populate empty element fields when the fields are optional but do not have default or fixed values.  
  
 For information about configuring the XML Assembler pipeline component, see [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md).  
  
## In This Section  
  
-   [Character Encoding in the XML Assembler Pipeline Component](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)  
  
-   [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)  
  
-   [Unrecognized Messages in the XML Assembler Pipeline Component](../core/unrecognized-messages-in-the-xml-assembler-pipeline-component.md)  
  
-   [XML Information Set Elements in the XML Assembler Pipeline Component](../core/xml-information-set-elements-in-the-xml-assembler-pipeline-component.md)  
  
-   [Document Structure Enforcement in the XML Assembler Pipeline Component](../core/document-structure-enforcement-in-the-xml-assembler-pipeline-component.md)
