---
title: IBaseMessage Interface (COM)
TOCTitle: IBaseMessage Interface (COM)
ms:assetid: 8c4ef1bc-a131-41c6-8a7d-3884c2a9c4b4
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561289(v=BTS.80)
ms:contentKeyID: 51529575
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IBaseMessage Interface (COM)

 

Represents the basic composition of the message.

For a list of all members of this type, see [IBaseMessage Members](ibasemessage-members-com.md).


> [!NOTE]
> <P>For information on using this interface within managed code, see the <CODE>IBaseMessage Interface</CODE>.</P>



## Remarks

This interface must be implemented for messages that get published to the database and delivered to the orchestration. The component needs to use the [CreateMessage](ibasemessagefactory-createmessage-method-com.md) method of the [IBaseMessageFactory](ibasemessagefactory-interface-com.md) interface to create a new message object in memory.

## See Also

[IBaseMessage Members (COM)](ibasemessage-members-com.md)

