---
description: "Learn more about: IBTTransportConfig.RemoveReceiveEndpoint Method (COM)"
title: IBTTransportConfig.RemoveReceiveEndpoint Method (COM)
TOCTitle: IBTTransportConfig.RemoveReceiveEndpoint Method (COM)
ms.topic: reference
ms:assetid: fdd25340-3319-4df2-8b3b-bda75280f346
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562137(v=BTS.80)
ms:contentKeyID: 51533779
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportConfig.RemoveReceiveEndpoint Method (COM)

 

Removes the URL from the list of URL addresses that the adapters listen to.

## Syntax

``` c++
  
HRESULT IBTTransportConfig::RemoveReceiveEndpoint(  
BSTR  
bstrURL  
);  
  
```

``` vb
  
Sub RemoveReceiveEndpoint(  
bstrURL  
 As String  
)  
  
```

## Remarks

**Parameters**

*bstrURL*  
\[in\] String that contains the URL the adapter needs to listen to.

*bstrURL*  
**String** that contains the URL the adapter needs to listen to.

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


**Remarks**

This method is called by the BizTalk Server Messaging Engine.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportConfig Interface (COM)](ibttransportconfig-interface-com.md)  
[IBTTransportConfig Members (COM)](ibttransportconfig-members-com.md)

