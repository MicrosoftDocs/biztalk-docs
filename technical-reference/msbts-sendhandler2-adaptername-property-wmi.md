---
title: MSBTS_SendHandler2.AdapterName Property (WMI)
TOCTitle: MSBTS_SendHandler2.AdapterName Property (WMI)
ms:assetid: 30c59145-1eb6-4342-8355-f861058aa5af
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559467(v=BTS.80)
ms:contentKeyID: 51527182
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendHandler2.AdapterName Property (WMI)

 

This property contains the name of the adapter used by the given instance. This property is required for instance creation.

## Syntax

``` 
  
stringAdapterName;  
```

## Remarks

This property can be written during instance creation. After that it is read only.

The maximum length for this property is 256 characters.


> [!NOTE]
> <P>The adapter name must be in upper case or the instance will fail.</P>



## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

