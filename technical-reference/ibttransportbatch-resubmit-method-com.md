---
title: IBTTransportBatch.Resubmit Method (COM)
TOCTitle: IBTTransportBatch.Resubmit Method (COM)
ms:assetid: 5c026cd0-08f9-4c70-a73f-8ebe5b116559
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560356(v=BTS.80)
ms:contentKeyID: 51528298
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.Resubmit Method (COM)

 

Adds a message to the batch to be resubmitted.

## Syntax

``` c++
  
        HRESULT IBTTransportBatch::Resubmit(  
        IBaseMessage*  
        pIndoc,  
DATEdtTimeStamp);  
```

``` vb
  
        Sub Resubmit(  
        pIndoc  
         As IBaseMessage,  
dtTimeStamp As Date)  
```

## Remarks

**Parameters**

*pIndoc*  
\[in\] Reference to a **IBaseMessage** object/interface that contains the message to be added to the batch.

*pIndoc*  
**IBaseMessage** object/interface that contains the message to be added to the batch.

*dtTimeStamp*  
\[in\] Date type that contains the time the message should be redelivered to this adapter.

*dtTimeStamp*  
**Date** that contains the message should be redelivered to this adapter.

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


**Remarks**

This method should only be called on send-side.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

