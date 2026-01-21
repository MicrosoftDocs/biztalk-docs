---
description: "Learn more about: IBTTransportProxy.GetBatch Method (COM)"
title: IBTTransportProxy.GetBatch Method (COM)
TOCTitle: IBTTransportProxy.GetBatch Method (COM)
ms:assetid: 484a32a6-be4c-4d6e-8457-2a6e94996daf
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559926(v=BTS.80)
ms:contentKeyID: 51527736
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBTTransportProxy.GetBatch Method (COM)

 

Gets a new transport proxy batch.

## Syntax

``` c++
  
        HRESULT IBTTransportProxy::GetBatch(  
        IBTBatchCallBack*  
        pCallBack,  
VARIANTvCallbackCookie,  
IBTTransportBatch**ppBatch);  
```

``` vb
  
        Function GetBatch(  
        pCallBack  
         As IBTBatchCallBack,  
vCallbackCookie As Variant) As IBTTransportBatch  
```

## Remarks

**Parameters**

*pCallBack*  
\[in\] Reference to a **IBTBatchCallBack** object/interface. The callback will be made to this interface after the [IBTTransportBatch.Done Method (COM)](ibttransportbatch-done-method-com.md) method has been called on the batch and the batch has been processed. The [IBTTransportBatch.Done Method (COM)](ibttransportbatch-done-method-com.md) method is a low cost method call since it posts the batch to the thread pool. The callback will be made once the thread pool has finished processing the batch. This parameter cannot be set to NULL.

*pCallBack*  
**IBTBatchCallBack** object/interface. The callback will be made to this interface after the [IBTTransportBatch.Done Method (COM)](ibttransportbatch-done-method-com.md) method has been called on the batch and the batch has been processed. The [IBTTransportBatch.Done Method (COM)](ibttransportbatch-done-method-com.md) method is a low cost method call since it posts the batch to the thread pool. The callback will be made once the thread pool has finished processing the batch. This parameter can be set to NULL.

*vCallbackCookie*  
\[in\] Variant that contains the callback cookie. The cookie will be passed back to the adapter when the callback is called on the [IBTBatchCallBack Interface (COM)](ibtbatchcallback-interface-com.md) interface. This parameter can be set to a variant of type VT\_EMPTY.

*vCallbackCookie*  
**Variant** that contains the callback cookie. The cookie will be passed back to the adapter when the callback is called on the [IBTBatchCallBack Interface (COM)](ibtbatchcallback-interface-com.md) interface. This parameter can be set to a variant of type VT\_EMPTY.

*ppBatch*  
\[out,retval\] Pointer to hold the reference to the returned **IBTTransportBatch** object/interface, which will contain the new batch.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns a [IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md) containing the new batch.

**Error Values**

This method returns an HRESULT containing one of the values in the following table.

This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>S_OK</td>
<td>The method completed successfully.</td>
</tr>
<tr class="even">
<td>BTS_E_MESSAGING_SHUTTING_DOWN</td>
<td>The messaging engine is shutting down.</td>
</tr>
<tr class="odd">
<td>E_INVALIDARG</td>
<td>A parameter that is not valid was detected.</td>
</tr>
</tbody>
</table>


**Remarks**

The adapter can use the callback pointer, a cookie parameter, or a combination of the parameters in order to correlate a particular batch to the internal data structures for the adapter. This method is intended to be as flexible as possible so as not to restrict the internal programming model of the adapter.

The batch is atomic with respect to the MessageBox. If a batch fails, none of the work will be committed to the MessageBox.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportProxy Interface (COM)](ibttransportproxy-interface-com.md)  
[IBTTransportProxy Members (COM)](ibttransportproxy-members-com.md)

