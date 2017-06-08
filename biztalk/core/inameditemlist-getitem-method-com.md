---
title: "INamedItemList.GetItem Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d61bd524-0f71-4ad9-91b1-b14a6e2f3ce2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# INamedItemList.GetItem Method (COM)
Accesses the items in the list.  
  
## Syntax  
  
```cpp  
  
        HRESULT INamedItemList::GetItem(  
        LONG  
        nIndex,  
INamedItem**ppRet);  
```  
  
```vb  
  
Function GetItem(  
nIndex  
 As Long  
) As INamedItem  
  
```  
  
#### Parameters  
 *nIndex*  
 [in] Integer that contains the location in the index.  
  
 *nIndex*  
 **Long** that contains the location in the index.  
  
 *ppRet*  
 [out,retval] Pointer to hold the reference to the returned **INamedItem** object/interface, which will contain the item located at the *nindex* value.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns a **INamedItem** that contains the named item at the index location.  
  
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
 [INamedItemList Interface (COM)](../core/inameditemlist-interface-com.md)   
 [INamedItemList Members (COM)](../core/inameditemlist-members-com.md)