---
title: "Promote Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.editor.props.promote"
helpviewer_keywords: 
  - "BizTalk Editor, Promote Properties dialog box"
  - "properties, promoting"
  - "promoting properties, configuring"
  - "Promote Properties dialog box [BizTalk Editor]"
ms.assetid: 569f7acf-2c96-4f1e-a7a1-ccf1c893084c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Promote Properties Dialog Box
Use the **Promote Properties** dialog box to manage both types of property promotion: distinguished fields and property fields, where each type of promoted property is managed using its own tab on the right side of the dialog box.  
  
> [!NOTE]
>  Promoted properties are restricted to non-repeating elements/attributes.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Schema tree**|Find and select the relevant record or field that you want to promote by using either property promotion technique.|  
|**Distinguished Fields** tab|Manage the distinguished field property promotions for the schema being edited.|  
|**Property Fields** tab|Manage the property schemas and property field promotions for the schema being edited.|  
|**Add**|Add a record or field as a promoted property, by using either the distinguished field or property field technique, depending on which tab is displayed.|  
|**Remove**|Remove the selected property promotion of the type associated with the currently displayed tab; either a distinguished field promotion or a property field promotion.|  
|**Update**|Replace the XPath of the promoted property that is currently selected with the XPath of the node that is currently selected in the schema tree.|  
|**Clear All**|Remove all property promotions of the type associated with the currently displayed tab; either all distinguished field promotions or all property field promotions.<br /><br /> This is the same as individually removing all property promotions of the relevant type.|  
|**Property** column of the **Distinguished Fields** tab|Display a list of the properties that have been promoted as distinguished fields.|  
|**Node Path** column of the **Distinguished Fields** tab|Display the XPath within the schema to the corresponding promoted property.|  
|**Add property schema button**<br /><br /> ![](../core/media/ebiz-tut-addpropertybttn.gif "ebiz_tut_addpropertybttn")|When the **Property Fields** tab is displayed, open the **BizTalk Type Picker** dialog box so that you can select a property schema to be added to the **Property Schemas List**.|  
|**Remove property schema button**<br /><br /> ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete")|When the **Property Fields** tab is displayed, remove the property schema currently selected in the **Property****Schemas List**, if any.|  
|**Prefix** column of **Property Schemas List** of the **Property Fields** tab|When the **Property Fields** tab is displayed, show the namespace prefix assigned to the corresponding property schema. Also, you can change the generated namespace prefix by editing it in place.|  
|**Namespace** column of **Property Schemas List** of the **Property Fields** tab|When the **Property Fields** tab is displayed, show the namespace URI of the corresponding property schema.|  
|**Location** column of **Property Schemas List** of the **Property Fields** tab|When the **Property Fields** tab is displayed, show the relative file location of the corresponding property schema.|  
|**Property** column of **Property Fields List** of the **Property Fields** tab|When the **Property Fields** tab is displayed, provide a drop-down list from which you can select a field within one of the property schemas into which the record or field data will be promoted.|  
|**Node Path** column of **Property Fields List** of the **Property Fields** tab|When the **Property Fields** tab is displayed, show the XPath within the schema of the record or field to be promoted into the corresponding property schema field.<br /><br /> Use the ellipsis (**...**) button to the right of the cells in this column to open the **Edit Instance XPath** dialog box, in which you can change the record or field to be promoted by providing an alternative XPath.|  
  
## See Also  
 [Promoting Properties](../core/promoting-properties.md)   
 [Property Schemas](../core/property-schemas.md)