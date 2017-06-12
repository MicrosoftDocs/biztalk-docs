---
title: "IBTTransportBatch.MoveToSuspendQ Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d20040f1-9194-4d51-98eb-55229a1e9d01
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.MoveToSuspendQ Method (COM)
Adds a message to the batch to be suspended.  
  
## Syntax  
  
```cpp  
  
            HRESULT IBTTransportBatch::MoveToSuspendQ(  
            IBaseMessage*  
            pIndoc,  
);  
```  
  
```vb  
  
            Sub MoveToSuspendQ(  
            pIndoc  
             As IBaseMessage,  
)  
```  
  
## Remarks  
 **Parameters**  
  
 *pIndoc*  
 [in] Reference to a **IBaseMessage** object/interface that contains the message to be suspended.  
  
 *pIndoc*  
 **IBaseMessage** object/interface that contains the message to be suspended.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)