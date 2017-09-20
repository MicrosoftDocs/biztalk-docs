---
title: "Custom Type Converter for Adapter Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60e94dde-d29d-43ff-84b0-b2ba86851151
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Type Converter for Adapter Configuration
Like the custom editor, the custom type converter overrides the **System.ComponentModel.TypeConverter** class of one of its children. Here, the converter adds formatting to the value to be persisted but does not appear on the property page. The **ConvertFrom** method adds square brackets around the string value and the **ConvertTo** method removes them.  
  
 The following code is the class definition for the custom type converter:  
  
```  
using System;  
using System.ComponentModel;  
  
namespace AdapterManagement.ComponentModel {  
  
   public class DesignerTypeConverter : StringConverter {  
  
      public override bool CanConvertTo(ITypeDescriptorContext context, Type destinationType) {  
         return (typeof(String) == destinationType) || base.CanConvertTo (context, destinationType);  
      }  
  
      public override object ConvertTo(ITypeDescriptorContext context, System.Globalization.CultureInfo culture, object value, Type destinationType) {  
         if (typeof(String) == destinationType && value is String) {  
            return ((String)value).TrimStart('[').TrimEnd(']');  
         }  
         return base.ConvertTo (context, culture, value, destinationType);  
      }  
  
      public override bool CanConvertFrom(ITypeDescriptorContext context, Type sourceType) {  
         return (typeof(String) == sourceType) || base.CanConvertFrom (context, sourceType);  
      }  
  
      public override object ConvertFrom(ITypeDescriptorContext context, System.Globalization.CultureInfo culture, object value) {  
         if (value is String) {  
            return "["+(String)value+"]";  
         }  
         return base.ConvertFrom (context, culture, value);  
      }  
   }  
}  
```  
  
## See Also  
 [Custom Adapter Configuration Designer](../core/custom-adapter-configuration-designer.md)   
 [Custom Drop-Down Editor for Adapter Configuration](../core/custom-drop-down-editor-for-adapter-configuration.md)   
 [Custom Modal Dialog Editor for Adapter Configuration](../core/custom-modal-dialog-editor-for-adapter-configuration.md)   
 [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md)