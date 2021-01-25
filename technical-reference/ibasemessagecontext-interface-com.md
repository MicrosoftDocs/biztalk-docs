---
description: "Learn more about: IBaseMessageContext Interface (COM)"
title: IBaseMessageContext Interface (COM)
TOCTitle: IBaseMessageContext Interface (COM)
ms:assetid: b67fc3aa-4326-4c45-af54-a8e24553fc66
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578256(v=BTS.80)
ms:contentKeyID: 51530692
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IBaseMessageContext Interface (COM)

 

Provides access to the properties of the message and allows promotion of the properties.

For a list of all members of this type, see [IBaseMessageContext Members](ibasemessagecontext-members-com.md).


> [!NOTE]
> <P>For information on using this interface within managed code, see the <CODE>IBaseMessageContext Interface</CODE>.</P>



## Remarks

This interface encapsulates the message context, which is essentially a property bag for storing object properties. The context object is contained within the message.

Notice that existing properties never have a NULL value. A NULL value means that the property does not exist. For example:

  - Attempting to set (or promote) a property value to NULL deletes the property with S\_OK.

  - Attempting to read a nonexistent property returns NULL with S\_OK.

  - For predicate-related interfaces, "x:a=NULL" (VT\_NULL), which is the same as the hypothetical NotExists(x:a) predicate, is the test for nonexistence of a property x:a.

Multivalued property values are still contained in the same single variant value (pVar).

## See Also

[IBaseMessageContext Members (COM)](ibasemessagecontext-members-com.md)

