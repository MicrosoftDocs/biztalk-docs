---
title: "Known Issues with Schema Generation and Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df1eaa6c-0d3e-4aec-9de0-8b9817b7bb97
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with Schema Generation and Validation
This topic provides information about known issues with schema generation and validation.  
  
## An instance message generated for a positional record with tags could be incorrect  
 For positional records, the tag can be within a field or can span between fields. In either case, the instance generated will not be valid and will cause a failure in the Parsing Engine during the parsing stage.  
  
 If the tag is not part of any children (child records or child fields), this problem will not occur.  
  
 To work around this issue, include the actual value of the tag as the default in the schema. In the flat file extension of the BizTalk Editor, you can set the **Fixed Value** or **Default Value** property of the appropriate positional field with the value of the tag.  
  
## An instance message generated for a field with some restrictions may not pass validation  
 When you generate an instance message from a schema that contains one or more **Field Element** and **Field Attribute** nodes that have data types that have been derived using the restriction mechanism, such as when the **Pattern** property is used, the sample data generated for such fields may not conform to the requirements of the restriction, thereby preventing successful validation of that instance message using the same schema from which it was generated.  
  
## An instance message generated for a schema that contains an infinite loop may not be valid.  
 Your schema can contain an infinite loop when it contains a circular reference to a node with a **Min Occurs** property value greater than or equal to one, essentially preventing a termination condition. Instance message generation will artificially terminate so that the generation operation can complete, but the produced instance message will thereby not conform to the schema from which it was generated. Such schemas are usually suspect.  
  
## Validation of XML instance fails for document schema which has the target namespace="<http://www.w3.org/XML/1998/namespace>"  
 The HYPERLINK "<http://www.w3.org/XML/1998/namespace>" is a reserved namespace whose prefix should be “XML”. You can manually edit the prefix to “XML”.

## See also
More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
