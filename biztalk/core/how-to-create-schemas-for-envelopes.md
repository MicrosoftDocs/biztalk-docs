---
description: "Learn more about: Create Schemas for Envelopes"
title: "How to Create Schemas for Envelopes"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Create Schemas for Envelopes

## Overview
After creating an XML message schema as described in [Creating Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md), set the **Envelope** property of the **Schema** node to **Yes**. Depending on certain characteristics of your envelope schema, such as whether there are multiple root nodes, you will need to set several other envelope-specific properties. For more information, see [Envelope Schemas](../core/envelope-schemas.md).  

 The body XPath property of the envelope points to the element that contains the document elements. The actual element where the XPath points to does not belong to the document.  

## See Also  
- [Managing Schemas Within Projects](../core/managing-schemas-within-projects.md)
- **Envelope** property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
