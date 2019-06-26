---
title: IBTDTCCommitConfirm.DTCCommitConfirm Method (COM)
TOCTitle: IBTDTCCommitConfirm.DTCCommitConfirm Method (COM)
ms:assetid: 6e4edc24-f3e0-4c31-aec7-abb8ab929f53
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560716(v=BTS.80)
ms:contentKeyID: 51528786
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTDTCCommitConfirm.DTCCommitConfirm Method (COM)

 

Notifies the BizTalk Server Messaging Engine of the outcome of a DTC transaction that the adapter committed.

## Syntax

``` c++
  
        HRESULT IBTDTCCommitConfirm::DTCCommitConfirm(  
        IUnknown*  
        pTransaction,  
BOOLbCommitSuccessful);  
```

``` vb
  
        Sub DTCCommitConfirm(  
        pTransaction  
         As IUnknown,  
bCommitSuccessful As Boolean)  
```

## Remarks

**Parameters**

*pTransaction*  
\[in\] Pointer to the **IUnknown** interface that contains the transaction that was committed.

*pTransaction*  
**IUnknown** that contains the transaction that was committed.

*bCommitSuccessful*  
\[in\] Boolean that contains the commit successful. **true** to indicate that the commit was successful; otherwise, **false**.

*bCommitSuccessful*  
**Boolean** that contains the commit successful. **true** to indicate that the commit was successful; otherwise, **false**.

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
</tbody>
</table>


**Requirements**

**Platforms:**  Windows

## See Also

[IBTDTCCommitConfirm Interface (COM)](ibtdtccommitconfirm-interface-com.md)  
[IBTDTCCommitConfirm Members (COM)](ibtdtccommitconfirm-members-com.md)

