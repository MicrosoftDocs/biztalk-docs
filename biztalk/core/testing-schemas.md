---
title: "Testing Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2e28b7c-9d0c-4336-8bee-4599d41a57f4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Testing Schemas
After you have created your schema, you may want to validate that it describes the XML structure you intend it to describe. You can perform the following three operations on your schema to validate it:  
  
- **Instance generation**. This operation generates an instance message from a schema, creating test data to accompany the XML elements and attributes specified by the schema.  
  
- **Schema validation**. This operation validates the internal consistency of a schema, assuring that it conforms to the XML Schema definition (XSD) language schema standard.  
  
- **Instance validation**. This operation validates a given instance message against a schema.  
  
  All three of these operations are useful for testing your schemas before putting them into use in a production environment.  
  
  This section describes these operations in greater detail.  
  
## In This Section  
  
-   [How to Validate Schemas in Visual Studio](../core/how-to-validate-schemas-in-visual-studio.md)  
  
-   [How to Validate Instance Messages](../core/how-to-validate-instance-messages.md)  
  
-   [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md)