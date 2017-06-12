---
title: "IBTTransportConfig.AddReceiveEndpoint Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d215daf8-c25b-4601-af3d-ded7cddde612
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportConfig.AddReceiveEndpoint Method (COM)
Adds a new URL address that the adapter should listen on for incoming messages.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransportConfig::AddReceiveEndpoint(  
        BSTR  
        bstrURL,  
IPropertyBag*pConfig,  
IPropertyBag*pBizTalkConfig);  
```  
  
```vb  
  
        Sub AddReceiveEndpoint(  
        bstrURL  
         As String,  
pConfig As IPropertyBag,  
pBizTalkConfig As IPropertyBag)  
```  
  
## Remarks  
 **Parameters**  
  
 *bstrURL*  
 [in] String that contains the URL the adapter should listen on.  
  
 *bstrURL*  
 **String** that contains the URL the adapter should listen on.  
  
 *pConfig*  
 [in] Reference to a **IPropertyBag** object/interface that contains the configuration for this URL.  
  
 *pConfig*  
 **IPropertyBag** object/interface that contains the configuration for this URL.  
  
 *pBizTalkConfig*  
 [in] Reference to a **IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities that indicate whether the port is one way or two way. This is indicated by the property **TwoWayReceivePort**.  
  
 *pBizTalkConfig*  
 **IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities that indicate whether the port is one way or two way. This is indicated by the property **TwoWayReceivePort**.  
  
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