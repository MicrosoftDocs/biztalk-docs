---
title: "Property Managers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 823352a0-e397-464a-a163-1dbf8feea8d7
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Property Managers
Property Managers allow an extension to add custom properties (generally as XSD annotations) to elements and attributes in the XSD representation of the schema, as well as extending the Properties window to include the custom properties associated with the extension.  
  
 A Property Manager is an object that implements the **IPropertyManager** interface, a reference to which is obtained by calling **IExtension.GetPropertyManager**, and passing an **ITreeNode** object as the input parameter. Typically the extension provides one **IPropertyManager** object for each **ITreeNode** object. The Property Manager is responsible for the collection of custom properties for that **ITreeNode** object.  
  
 A custom property is represented by a **System.ComponentModel.PropertyDescriptor** object, which can be obtained from the collection returned by the **IPropertyManager.GetProperties** method.  
  
 Using **PropertyDescriptor** objects to represent the custom properties associated with the extension facilitates integration with the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window. When **PropertyDescriptor** objects are used, it is easy for BizTalk Editor to integrate the custom properties of the extension into the set of standard node properties already being integrated into the Properties window. Custom property information such as the display name, the display value, the type of property control, the property description, and the property category is obtained from the **PropertyDescriptor** object.  
  
 Custom properties are stored in the XSD representation of the schema as attributes of an element within the annotation element within the element corresponding to the relevant node in the schema tree. Each custom property of a schema tree node can be an attribute of a common element, or alternatively, each can have its own associated element.  
  
## See Also  
 [Extending BizTalk Editor](../core/extending-biztalk-editor.md)