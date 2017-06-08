---
title: "BizTalk Framework Assembler Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.BTFAsmComp"
ms.assetid: 00179f6d-75ba-4cac-9136-dd1c1b2c05bf
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Framework Assembler Pipeline Component Properties
Use the BizTalk Framework assembler pipeline component to serialize the BizTalk Framework envelope and contents onto the message before transmission, resend in the event that a receipt does not arrive in the allotted time period, and receive and process the receipts when they come to delete the message instance.  
  
 The BizTalk Framework assembler pipeline component is intended for use in the Assemble stage of the Send pipeline.  
  
 The properties for the BizTalk Framework assembler pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable BizTalk Framework assembler pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add processing instructions text**|Allow the assembled XML documents to contain processing instructions as a value of this property. This also allows documents to contain instructions for applications. **Note:**  Processing instruction text should conform to the W3C XML processing instruction standards. <br /><br /> Default value: None|  
|**Add XML declaration**|Add an XML declaration to an outgoing message. When True, the following XML declaration is added to the outgoing message `<?xml version='1.0' encoding='UTF8'>`. The encoding specified depends on the encoding used by the BizTalk Framework assembler, which honors the specific runtime properties carrying the encoding information.<br /><br /> Default value: True|  
|**Delivery receipt address**|Indicate the address to which the delivery receipt for the BizTalk Framework document should be sent.<br /><br /> Default value: None|  
|**Delivery receipt address type**|Indicate the type of address to which the delivery receipt for the BizTalk Framework document should be sent.<br /><br /> Default value: biz: **Note:**  The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk 2000 and 2002, and for interoperability with those systems, the prefix is provided as a default here. For example, type = "biz:OrganizationName", (src&#124;dest) = "Party1".|  
|**Delivery receipt send by time**|Indicate the time (in minutes) by which the delivery receipt for the BizTalk Framework document must be received.<br /><br /> Default value: 30|  
|**Destination address**|Identify the destination address.<br /><br /> Default value: None|  
|**Destination address type**|Indicate the destination address type.<br /><br /> Default value: biz: **Note:**  The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk 2000 and 2002, and for interoperability with those systems, the prefix is provided as a default here. For example, type = "biz:OrganizationName", (src&#124;dest) = "Party1".|  
|**Document schemas**|Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: (Collection) Empty collection|  
|**Document topic**|Identify a URI reference that uniquely identifies the overall purpose of the BizTalk Framework document.<br /><br /> Default value: None|  
|**Envelope schemas**|Indicate the namespace and typename of the schema or schemas that will be applied to the envelope. For more information, see [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Default value: (Collection), BTF2Schemas.btf2_envelope|  
|**Generate delivery receipt request**|Indicate whether the delivery receipt request for the BizTalk Framework document should be generated. This is used to enable reliable messaging for the BizTalk Framework.<br /><br /> Default value: False|  
|**Message time to live (in minutes)**|Specify the amount of time (in minutes) that the message will be valid.<br /><br /> Default value: 30|  
|**Add Processing instructions**|Specify how XML processing instructions are handled in the XML instance document.<br /><br /> Append: The value of **Add Processing Instructions Text** should append to pre-existing processing instructions in the message.<br /><br /> Create New: Thevalue of **Add Processing Instructions Text** entered in the field should overwrite or replace any pre-existing processing instructions in the message.<br /><br /> If **Create New** is selected, then **Add Processing Instructions Text** must contain valid processing instructions.<br /><br /> Ignore: If processing instructions text exists in the message, it is removed.<br /><br /> Default Value: Append|  
|**Source address**|Identify the source address.<br /><br /> Default value: None|  
|**Source address type**|Indicate the source address type.<br /><br /> Default value: biz: **Note:**  The biz: prefix was used to signify organization identifiers for the source and destination endpoints in BizTalk 2000 and 2002, and for interoperability with those systems, the prefix is provided as a default here. For example, type = "biz:OrganizationName", (src&#124;dest) = "Party1".|  
|**Target charset**|Identify the character set used for encoding of outgoing messages.<br /><br /> Default value: (None)|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md)   
 [How to Open a Pipeline](../core/how-to-open-a-pipeline.md)   
 [How to Add a Component to a Pipeline](../core/how-to-add-a-component-to-a-pipeline.md)   
 [How to Set Pipeline Component Properties](../core/how-to-set-pipeline-component-properties.md)   
 [How to Use the Schema Collection Property Editor](../core/how-to-use-the-schema-collection-property-editor.md)   
 [How to Save a Pipeline](../core/how-to-save-a-pipeline.md)   
 [How to Use the Toolbox](../core/how-to-use-the-toolbox.md)   
 [How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md)   
 [How to Read Pipeline Component Properties](../core/how-to-read-pipeline-component-properties.md)