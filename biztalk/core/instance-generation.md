---
description: "Learn more about: Instance Generation"
title: "Instance Generation"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Instance Generation
BizTalk Editor invokes the **IInstanceGenerator.GenerateInstance** method of an extension when the following conditions are met:  
  
-   The extension is set as standard by using the **Standard** property of the **Schema** node.  
  
-   On the **Property Pages** dialog box associated with the schema, the **Generate Instance Output Type** property is set to **Native.**  
  
-   On the **Property Pages** dialog box associated with the schema, the **Output Instance Filename** property is set to the name of the file that the output instance will be saved to.  
  
> [!NOTE]
>  If the **Output Instance Filename** property is not set, a default file name in a temporary folder is used for the generated instance message, and a link to it is provided in the Output window.  
  
 Before the **IInstanceValidator.ValidateInstance** method is called, BizTalk Editor generates a sample XML instance message, and then passes it and the file specified in the **Output Instance Filename** property, or a default file name, to that method.  
  
 If errors occur, error messages are returned as an array of **IValidationInfo** objects, and are displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Task List window.  
  
## See Also  
 [Extending BizTalk Editor](../core/extending-biztalk-editor.md)
