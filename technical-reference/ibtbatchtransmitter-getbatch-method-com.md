---
title: IBTBatchTransmitter.GetBatch Method (COM)
TOCTitle: IBTBatchTransmitter.GetBatch Method (COM)
ms:assetid: 36be99fb-e7b0-442a-b487-e8e64dbb79d1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559589(v=BTS.80)
ms:contentKeyID: 51527342
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTBatchTransmitter.GetBatch Method (COM)

 

Returns a new batch that will be used by the BizTalk Server Messaging Engine, which will push messages to be transmitted into the batch.

## Syntax

``` c++
  
HRESULT IBTBatchTransmitter::GetBatch(  
IBTTransmitterBatch**  
ppBatch  
);  
  
```

``` vb
  
Function GetBatch
() As IBTTransmitterBatch  
  
```

## Remarks

**Parameters**

*ppBatch*  
\[out,retval\] Pointer to hold the reference to the returned **IBTTransmitterBatch** object/interface, which will contain the new adapter batch.

None.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the [IBTTransmitterBatch](ibttransmitterbatch-interface-com.md) containing the new adapter batch.

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


**Requirements**

**Platforms:**  Windows

## See Also

[IBTBatchTransmitter Interface (COM)](ibtbatchtransmitter-interface-com.md)  
[IBTBatchTransmitter Members (COM)](ibtbatchtransmitter-members-com.md)

