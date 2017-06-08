---
title: "IBTTransportConfig.RemoveReceiveEndpoint Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdd25340-3319-4df2-8b3b-bda75280f346
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportConfig.RemoveReceiveEndpoint Method (COM)
Removes the URL from the list of URL addresses that the adapters listen to.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportConfig::RemoveReceiveEndpoint(  
BSTR  
bstrURL  
);  
  
```  
  
```vb  
  
Sub RemoveReceiveEndpoint(  
bstrURL  
 As String  
)  
  
```  
  
## Remarks  
 **Parameters**  
  
 *bstrURL*  
 [in] String that contains the URL the adapter needs to listen to.  
  
 *bstrURL*  
 **String** that contains the URL the adapter needs to listen to.  
  
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
 [IBTTransportConfig Interface (COM)](../core/ibttransportconfig-interface-com.md)   
 [IBTTransportConfig Members (COM)](../core/ibttransportconfig-members-com.md)