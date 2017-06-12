---
title: "IBTTransportControl.Initialize Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 861280f6-75e9-4f7b-a5ad-4175a1bb51a9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportControl.Initialize Method (COM)
Initializes the adapter.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportControl::Initialize(  
IBTTransportProxy*  
pTransProxy  
);  
  
```  
  
```vb  
  
Sub Initialize(  
pTransProxy  
 As IBTTransportProxy  
)  
  
```  
  
## Remarks  
 **Parameters**  
  
 *pTransProxy*  
 [in] Reference to a **IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.  
  
 *pTransProxy*  
 **IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
 **Remarks**  
  
 This method is called by the BizTalk Server Messaging Engine.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportControl Interface (COM)](../core/ibttransportcontrol-interface-com.md)   
 [IBTTransportControl Members (COM)](../core/ibttransportcontrol-members-com.md)