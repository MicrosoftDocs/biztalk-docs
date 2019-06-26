---
title: IBaseMessage.AddPart Method (COM)
TOCTitle: IBaseMessage.AddPart Method (COM)
ms:assetid: a29f9147-d283-4928-9a75-297f854346ed
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577819(v=BTS.80)
ms:contentKeyID: 51530200
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.AddPart Method (COM)

 

Adds a part to the message.

## Syntax

``` c++
  
        HRESULT IBaseMessage::AddPart(  
        BSTR  
        bstrPartName,  
IBaseMessagePart*pPart,  
BOOLbIsBody);  
```

``` vb
  
        Sub AddPart(  
        bstrPartName  
         As String,  
pPart As IBaseMessagePart,  
bIsBody As Boolean)  
```

#### Parameters

*bstrPartName*  
\[in\] String that contains the part name.

*bstrPartName*  
**String** that contains the part name.

*pPart*  
\[in\] Reference to a **IBaseMessagePart** object/interface that contains the part.

*pPart*  
**IBaseMessagePart** object/interface that contains the part.

*bIsBody*  
\[in\] Boolean that identifies whether the part is a body part. **true** indicates the part is a body part; otherwise, **false**.

*bIsBody*  
**Boolean** that identifies whether the part is a body part. **true** indicates the part is a body part; otherwise, **false**.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

## Error Values

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


## Remarks

The part name must be unique within the message.

## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

