---
description: "Learn more about: Advanced Configuration Components for Adapters"
title: "Advanced Configuration Components for Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb31b996-6959-4b5a-9a9f-f48fd91a6180
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Advanced Configuration Components for Adapters
The BizTalk Adapter Framework supports a custom drop-down editor, a custom modal dialog editor, and a custom type converter. These custom design components are especially useful when taking user name and password information as input.  
  
 You can invoke a custom editor or type converter for a specific data field (element or attribute) in the configuration schema. As described in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help, the editor must be derived from **System.Drawing.Design.UITypeEditor** and the type converter from **System.ComponentModel.TypeConverter**.  
  
 An editor minimally overrides the **GetEditStyle** method to specify the kind of editor (**Modal** dialog, **DropDown** control, or **None** of the above) and the **EditValue** method to change the value with the editor.  
  
 A type converter typically overrides the **ConvertFrom**, **CanConvertFrom**, **ConvertTo**, **CanConvertTo**, **GetStandardValues**, **GetStandardValuesSupported**, and **GetStandardValuesExclusive**methods of the .NET Framework Class Library.  
  
## In This Section  
  
-   [Custom Adapter Configuration Designer](../core/custom-adapter-configuration-designer.md)  
  
-   [Custom Drop-Down Editor for Adapter Configuration](../core/custom-drop-down-editor-for-adapter-configuration.md)  
  
-   [Custom Modal Dialog Editor for Adapter Configuration](../core/custom-modal-dialog-editor-for-adapter-configuration.md)  
  
-   [Custom Type Converter for Adapter Configuration](../core/custom-type-converter-for-adapter-configuration.md)
