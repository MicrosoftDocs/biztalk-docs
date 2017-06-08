---
title: "IBTTransportConfig.UpdateEndpointConfig Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdb73a17-f39f-425c-8fd2-6a496f9717f9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportConfig.UpdateEndpointConfig Method (COM)
Updates the configuration of the URL.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransportConfig::UpdateEndpointConfig(  
        BSTR  
        bstrURL,  
IPropertyBag*pConfig,  
IPropertyBag*pBizTalkConfig);  
```  
  
```vb  
  
        Sub UpdateEndpointConfig(  
        bstrURL  
         As String,  
pConfig As IPropertyBag,  
pBizTalkConfig As IPropertyBag)  
```  
  
## Remarks  
 **Parameters**  
  
 *bstrURL*  
 [in] String that contains the URL that needs to be configured.  
  
 *bstrURL*  
 **String** that contains the URL that needs to be configured.  
  
 *pConfig*  
 [in] Reference to a **IPropertyBag** object/interface that contains the new configuration for the URL.  
  
 *pConfig*  
 **IPropertyBag** object/interface that contains the new configuration for the URL.  
  
 *pBizTalkConfig*  
 [in] Reference to a **IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities, which indicate whether the port is one way or two way.  
  
 *pBizTalkConfig*  
 **IPropertyBag** object/interface that contains the BizTalk Server configuration, specifically the port capabilities, which indicate whether the port is one way or two way.  
  
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