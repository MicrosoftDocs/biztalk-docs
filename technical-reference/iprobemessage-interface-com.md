---
title: IProbeMessage Interface (COM)
TOCTitle: IProbeMessage Interface (COM)
ms:assetid: a3683382-1ac3-493e-8bf7-96fa7ec0722c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577843(v=BTS.80)
ms:contentKeyID: 51530171
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IProbeMessage Interface (COM)

 

Defines the methods and properties for components that need probing functionality.

For a list of all members of this type, see [IProbeMessage Members (COM)](iprobemessage-members-com.md).


> [!NOTE]
> <P>For information on using this interface within managed code, see the <CODE>IProbeMessage Interface</CODE>.</P>



## Remarks

All components included in a stage configured for **FirstMatch** execution need to implement this interface before the messaging component checks to see if the message is recognizable. This behavior is used when several parser components are placed in one pipeline. The first parser that can recognize the message format is executed.

## See Also

[IProbeMessage Members (COM)](iprobemessage-members-com.md)

