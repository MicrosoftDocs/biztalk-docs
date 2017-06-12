---
title: "IBTTransportProxy.GetBatch Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 484a32a6-be4c-4d6e-8457-2a6e94996daf
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportProxy.GetBatch Method (COM)
Gets a new transport proxy batch.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransportProxy::GetBatch(  
        IBTBatchCallBack*  
        pCallBack,  
VARIANTvCallbackCookie,  
IBTTransportBatch**ppBatch);  
```  
  
```vb  
  
        Function GetBatch(  
        pCallBack  
         As IBTBatchCallBack,  
vCallbackCookie As Variant) As IBTTransportBatch  
```  
  
## Remarks  
 **Parameters**  
  
 *pCallBack*  
 [in] Reference to a **IBTBatchCallBack** object/interface. The callback will be made to this interface after the [IBTTransportBatch.Done Method (COM)](../core/ibttransportbatch-done-method-com.md) method has been called on the batch and the batch has been processed. The [IBTTransportBatch.Done Method (COM)](../core/ibttransportbatch-done-method-com.md) method is a low cost method call since it posts the batch to the thread pool. The callback will be made once the thread pool has finished processing the batch. This parameter cannot be set to NULL.  
  
 *pCallBack*  
 **IBTBatchCallBack** object/interface. The callback will be made to this interface after the [IBTTransportBatch.Done Method (COM)](../core/ibttransportbatch-done-method-com.md) method has been called on the batch and the batch has been processed. The [IBTTransportBatch.Done Method (COM)](../core/ibttransportbatch-done-method-com.md) method is a low cost method call since it posts the batch to the thread pool. The callback will be made once the thread pool has finished processing the batch. This parameter can be set to NULL.  
  
 *vCallbackCookie*  
 [in] Variant that contains the callback cookie. The cookie will be passed back to the adapter when the callback is called on the [IBTBatchCallBack Interface (COM)](../core/ibtbatchcallback-interface-com.md) interface. This parameter can be set to a variant of type VT_EMPTY.  
  
 *vCallbackCookie*  
 **Variant** that contains the callback cookie. The cookie will be passed back to the adapter when the callback is called on the [IBTBatchCallBack Interface (COM)](../core/ibtbatchcallback-interface-com.md) interface. This parameter can be set to a variant of type VT_EMPTY.  
  
 *ppBatch*  
 [out,retval] Pointer to hold the reference to the returned **IBTTransportBatch** object/interface, which will contain the new batch.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns a [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md) containing the new batch.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|BTS_E_MESSAGING_SHUTTING_DOWN|The messaging engine is shutting down.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
 **Remarks**  
  
 The adapter can use the callback pointer, a cookie parameter, or a combination of the parameters in order to correlate a particular batch to the internal data structures for the adapter. This method is intended to be as flexible as possible so as not to restrict the internal programming model of the adapter.  
  
 The batch is atomic with respect to the MessageBox. If a batch fails, none of the work will be committed to the MessageBox.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportProxy Interface (COM)](../core/ibttransportproxy-interface-com.md)   
 [IBTTransportProxy Members (COM)](../core/ibttransportproxy-members-com.md)