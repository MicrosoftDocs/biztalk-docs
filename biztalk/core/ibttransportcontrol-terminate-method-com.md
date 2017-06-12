---
title: "IBTTransportControl.Terminate Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0022ba49-0c5e-49af-8558-b5b032788687
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportControl.Terminate Method (COM)
Finishes processing any messages the adapter is currently processing and prepares for termination.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportControl::Terminate(  
);  
  
```  
  
```vb  
  
Sub Terminate()  
  
```  
  
## Remarks  
 **Parameters**  
  
 None.  
  
 None.  
  
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
  
 The adapter should not start any new work after this call, but may complete outstanding work items as necessary.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportControl Interface (COM)](../core/ibttransportcontrol-interface-com.md)   
 [IBTTransportControl Members (COM)](../core/ibttransportcontrol-members-com.md)