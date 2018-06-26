---
title: "How Node Name Characters Get Encoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6462856b-7a52-40c9-9aff-c0579130eec9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How Node Name Characters Get Encoded
If you use a character that is not allowed in a node name, BizTalk Editor prompts you, asking if you want to proceed with the disallowed character or characters encoded (**OK** or **Cancel**). If you proceed, each disallowed character is encoded as follows:  
  
- Disallowed characters are encoded as "*xDDDD\\*" where "DDDD" is the 4-digit hexadecimal Unicode representation of the character. For example, the space character (0x0020) is encoded as "*x0020\\*".  
  
- If two or more adjacent disallowed characters are encoded, only a single underscore character is used between them. For example, three spaces are encoded as "*x0020_x0020_x0020\\*" rather than "*x0020\__x0020\__x0020\\*".  
  
> [!NOTE]
>  You can disable prompting for node name encoding by setting the **Show Encode Warning Dialog** property to **False** in the BizTalk Editor folder of the **Options** dialog box, available on the **Tools** menu, or by selecting the **Do not show this dialog in the future** check box in the node name encoding dialog box. For more information about the options in this dialog box, see [Managing the Schema Tree View](../core/how-to-manage-the-schema-tree-view.md).  
  
 The schema tree view in BizTalk Editor displays node names by using the characters you type. BizTalk Mapper also displays the characters you have typed rather than the encoded version. In the XSD view of BizTalk Editor, and in the XSD file itself, the encoded node name is used. For example, if you name a node Purchase Order, it will be displayed as Purchase Order in the schema trees in both BizTalk Editor and BizTalk Mapper. In the XSD view of BizTalk Editor, the corresponding element node, when first inserted, will be as follows.  
  
```  
<element name="Purchase_x0020_Order" type="xs:string />  
  
```  
  
## See Also  
 [Node Name Property](../core/node-name-property.md)   
 [Which Node Name Characters Get Encoded](../core/which-node-name-characters-get-encoded.md)