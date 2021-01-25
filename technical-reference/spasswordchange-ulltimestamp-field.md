---
description: "Learn more about: SPasswordChange.ullTimeStamp Field"
title: SPasswordChange.ullTimeStamp Field
TOCTitle: SPasswordChange.ullTimeStamp Field
ms:assetid: cc7be835-44ee-4413-be15-ccb4b3422653
ms:mtpsurl: https://msdn.microsoft.com/library/Aa771884(v=BTS.80)
ms:contentKeyID: 51531263
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# SPasswordChange.ullTimeStamp Field

 

An integer containing a UTC timestamp in FILETIME format.

## Syntax

``` c++
  
public: ULONGLONG ullTimeStamp;  
```

## Remarks

If zero, then Enterprise Single Sign-On (ENTSSO) uses the current time.

## Requirements

**Platforms:**  Windows

## See Also

[SPasswordChange Structure (COM)](spasswordchange-structure-com.md)  
[SPasswordChange Members](spasswordchange-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

