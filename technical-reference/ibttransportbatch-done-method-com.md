---
description: "Learn more about: IBTTransportBatch.Done Method (COM)"
title: IBTTransportBatch.Done Method (COM)
TOCTitle: IBTTransportBatch.Done Method (COM)
ms.topic: reference
ms:assetid: b84d540f-c82d-4bef-b1a0-88ffce0475c0
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578288(v=BTS.80)
ms:contentKeyID: 51530765
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.Done Method (COM)

 

Posts the batch of work to the thread pool for the BizTalk Server Messaging Engine where it will be processed asynchronously.

## Syntax

``` c++
  
            HRESULT IBTTransportBatch::Done(  
            IUnknown*  
            pTransaction,   
);  
```

``` vb
  
            Sub Done(  
            pTransaction  
             As IUnknown,   
)  
```

## Remarks

**Parameters**

*pTransaction*  
\[in\] Pointer to the DTC transaction.

*pTransaction*  
**IUnknown** that contains the DTC transaction.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

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
<td>E_INVALIDARG</td>
<td>A parameter that is not valid was detected.</td>
</tr>
</tbody>
</table>


**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

