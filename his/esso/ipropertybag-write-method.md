---
title: "IPropertyBag.Write Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ba41d83-f462-4994-adb7-baeb11633789
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# IPropertyBag.Write Method
Writes the specified Single Sign-on property.  
  
## Syntax  
  
```csharp  
  
void Write(  
      string pszPpropName,   
      object pVar  
)  
```  
  
#### Parameters  
  
|Parameters|Reference|  
|----------------|---------------|  
|pszPropName|The name of the property to write.|  
|pVar|The value of the property to write.|  
  
## Remarks  
  
-   If you call QueryInterface on an SSO object, you can retrieve the IPropertyBag interface and use it to change the behavior of your current object.  
  
## See Also  
 [IPropertyBag Methods1](../esso/ipropertybag-methods1.md)   
 [Enterprise Single Sign-On Flags](../esso/enterprise-single-sign-on-flags.md)