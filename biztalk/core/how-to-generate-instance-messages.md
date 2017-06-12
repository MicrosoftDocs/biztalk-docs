---
title: "How to Generate Instance Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff74c67a-7e73-4153-9ec4-e6e50464ee92
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Generate Instance Messages
After you have constructed a schema, one way to check your work is to generate a sample instance message from the schema. In many ways, looking at an instance message is much more straightforward than looking at either the schema tree or the XML Schema definition (XSD) language representation of the schema. This is because the schema needs to describe all of the possible variations of the corresponding instance messages, and a specific instance message just needs to convey some data by using the format specified by the schema. The generated instance message is a sample and may not show all of the structures defined by the corresponding schema.  
  
### To explicitly specify a file to contain the generated instance message  
  
1.  In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Properties**.  
  
2.  If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.  
  
3.  In the **Output Instance Filename** property value field, either type the name of a file or use the ellipsis (**...**) button at the right end of the value field to browse for a file into which generated instance messages will be placed, and then click **Save**.  
  
### To specify the type of the generated instance message  
  
1.  In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Properties**.  
  
2.  If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.  
  
3.  In the **Generate Instance Output Type** property value field, use the drop-down list to select either **XML** or **Native** as the type of the instance message to be generated.  
  
     **XML** is the default value.  
  
### To generate a sample instance message for a schema  
  
1.  In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Generate Instance**.  
  
2.  In the Output window, view the results. Success and error messages are displayed in this window.  
  
> [!NOTE]
>  If the Output window and/or the Task List window did not open and display information about whether the instance generation succeeded or failed, you can open them manually. For more information about managing these windows, see [Managing Other Visual Studio Windows](../core/how-to-manage-other-visual-studio-windows.md).  
  
> [!NOTE]
>  If you do not specify a value for the **Root Reference** property, BizTalk Editor generates a sample instance message for the first root node in the schema. If you specify a value for the **Root Reference** property, BizTalk Editor generates a sample instance message for that root.  
  
> [!NOTE]
>  There are some cases instance messages generated from a particular schema may not pass validation with that same schema. For more information about such cases, see [Known Issues with Schema Generation and Validation](../core/known-issues-with-schema-generation-and-validation.md). Generally, you want to edit a generated instance message and change the data it contains so that it more realistically represents your scenario. Then use this modified instance message to validate your schema.  
  
## See Also  
 [Testing Schemas](../core/testing-schemas.md)   
 [Schema Validation](../core/schema-validation1.md)   
 [Instance Message Generation and Validation](../core/instance-message-generation-and-validation.md)