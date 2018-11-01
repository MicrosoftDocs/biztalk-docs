---
title: SStatus.bstrErrorMessage Field
TOCTitle: SStatus.bstrErrorMessage Field
ms:assetid: 65b4d7b7-6482-428e-ad40-e33bcb29d61c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa771250(v=BTS.80)
ms:contentKeyID: 51528548
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
---

# SStatus.bstrErrorMessage Field

 

A string that contains an error message.

## Syntax

``` c++
  
public: BSTR bstrErrorMessage;  
```

## Remarks

**bstrErrorMessage** Can be NULL. You must free **bstrEerrorMessage** after every use.

## Requirements

**Platforms:**  Windows

## See Also

[SStatus Structure (COM)](sstatus-structure-com.md)  
[SStatus Members](sstatus-members.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/en-us/library/aa704508\(v=bts.80\))

