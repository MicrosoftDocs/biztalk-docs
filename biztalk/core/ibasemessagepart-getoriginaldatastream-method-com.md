---
title: "IBaseMessagePart.GetOriginalDataStream Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2359b2e5-e574-41a1-9f56-aaa117825a4a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.GetOriginalDataStream Method (COM)
Retrieves the original uncloned version of the part data stream.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessagePart::GetOriginalDataStream(  
IStream**  
ppStream  
);  
  
```  
  
```vb  
  
Function GetOriginalDataStream() As IStream  
  
```  
  
#### Parameters  
 *ppStream*  
 [out,retval] Pointer to hold the reference to the returned **IStream** object/interface, which will contain the stream.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the uncloned version of the part data stream.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Remarks  
 The component should ensure safe multithreaded access to the stream when using this method.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessagePart Interface (COM)](../core/ibasemessagepart-interface-com.md)   
 [IBaseMessagePart Members (COM)](../core/ibasemessagepart-members-com.md)