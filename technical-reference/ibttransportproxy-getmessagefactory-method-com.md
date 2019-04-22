---
title: IBTTransportProxy.GetMessageFactory Method (COM)
TOCTitle: IBTTransportProxy.GetMessageFactory Method (COM)
ms:assetid: ce8dff51-a7b6-459c-a770-e5c29430970f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578487(v=BTS.80)
ms:contentKeyID: 51531448
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportProxy.GetMessageFactory Method (COM)

 

Gets the base message factory.

## Syntax

``` c++
  
HRESULT IBTTransportProxy::GetMessageFactory(  
IBaseMessageFactory**  
ppRet  
);  
  
```

``` vb
  
Function GetMessageFactory
() As IBaseMessageFactory  
  
```

## Remarks

**Parameters**

*ppRet*  
\[out,retval\] Pointer to hold the reference to the returned **IBaseMessageFactory** object/interface for the message factory.

None.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns an `IBaseMessageFactory` for the message factory.

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

The adapter should use the message factory to create messages.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportProxy Interface (COM)](ibttransportproxy-interface-com.md)  
[IBTTransportProxy Members (COM)](ibttransportproxy-members-com.md)

