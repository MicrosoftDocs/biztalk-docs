---
description: "Learn more about: IBTTransmitterBatch.BeginBatch Method (COM)"
title: IBTTransmitterBatch.BeginBatch Method (COM)
TOCTitle: IBTTransmitterBatch.BeginBatch Method (COM)
ms:assetid: 84cdad96-142d-40ea-b640-b310dd31dab8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561157(v=BTS.80)
ms:contentKeyID: 51529386
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
- vb
---

# IBTTransmitterBatch.BeginBatch Method (COM)

 

Initializes the batch.

## Syntax

``` c++
  
        HRESULT IBTTransmitterBatch::BeginBatch(  
        LONG*  
        pnMaxBatchSize,  
IUnknown**ppTransaction);  
```

``` vb
  
Function BeginBatch(  
pnMaxBatchSize  
 As Long  
) As IUnknown  
  
```

## Remarks

**Parameters**

*pnMaxBatchSize*  
\[out\] Pointer to an integer used to return the maximum number of messages the adapter will allow in this batch.

*pnMaxBatchSize*  
**Long** used to return the maximum number of messages the adapter will allow in this batch.

*ppTransaction*  
\[out,retval\] Address of a pointer to receive an **IUnknown** interface, which will contain the transaction that the Messaging Engine will use in agent interactions. This parameter may be **NULL**.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns a **IUnknown** that contains the transaction that the Messaging Engine will use in agent interactions. This parameter may be **NULL**.

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
</tbody>
</table>


**Remarks**

The BizTalk Server Messaging Engine calls this method prior to pushing messages into the batch.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransmitterBatch Interface (COM)](ibttransmitterbatch-interface-com.md)

