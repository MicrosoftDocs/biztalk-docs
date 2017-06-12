---
title: "IComponentUI.Validate Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99f52e7b-37cc-4c69-8f88-f92524577fbf
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IComponentUI.Validate Method (COM)
Verifies that all of the configuration properties are set correctly.  
  
## Syntax  
  
```cpp  
  
HRESULT IComponentUI::Validate(  
IUnknown**  
ppEnum  
);  
  
```  
  
```vb  
  
Function Validate() As IUnknown  
  
```  
  
#### Parameters  
 *ppEnum*  
 [out,retval] Address of a pointer to receive an **IUnknown** interface, which will contain the enumeration.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
## Remarks  
 This method is called by the Pipeline Designer prior to pipeline compilation.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IComponentUI Interface (COM)](../core/icomponentui-interface-com.md)