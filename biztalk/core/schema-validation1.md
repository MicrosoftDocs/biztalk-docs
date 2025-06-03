---
description: "Learn how the BizTalk Editor extension performs schema validation."
title: "Schema Validation1"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# About Schema Validation

If a BizTalk Editor extension provides an **ISchemaValidator** object, the framework will invoke **ISchemaValidator.ValidateSchema** when the user invokes the **Validate Schema** command, or during compilation when the user builds the BizTalk project containing the schema. The extension usually validates the custom properties, and can return error messages as an array of **IValidationInfo** objects. The error messages are displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Task List window, along with errors returned from BizTalk Editor compiler.  
  
## See Also

 [Extending BizTalk Editor](../core/extending-biztalk-editor.md)
