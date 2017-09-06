---
title: "How to Validate Instance Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f6302c6-b56b-4572-aa76-0f4c4599672a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Validate Instance Messages
After you have constructed a schema, you can check your work by validating a pre-existing instance message that you know is a good representation of such instance messages against the schema.  
  
 This topic provides step-by-step instructions for this validation task.  
  
### To validate an instance message against a schema  
  
1.  In Solution Explorer, right-click the schema, and then click **Properties**.  
  
2.  If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.  
  
3.  In the **Input Instance Filename** property value field, either type the name of a file or use the ellipsis (**...**) button at the right end of the value field to browse for a file that contains the instance message to be validated against the schema, and then click **Open**.  
  
4.  In **Solution Explorer**, right-click the schema name, and then click **Validate Instance**.  
  
5.  In the Output window, view the results. Success and error messages are displayed in this window.  
  
> [!NOTE]
>  There are some cases instance messages generated from a particular schema may not pass validation with that same schema. For more information about such cases, see [Known Issues with Schema Generation and Validation](../core/known-issues-with-schema-generation-and-validation.md). Generally, you will want to edit a generated instance message and change the data it contains so that it more realistically represents your scenario. Then use this modified instance message to validate your schema.  
  
## See Also  
 [Testing Schemas](../core/testing-schemas.md)   
 [Schema Validation](../core/schema-validation1.md)   
 [Instance Message Generation and Validation](../core/instance-message-generation-and-validation.md)