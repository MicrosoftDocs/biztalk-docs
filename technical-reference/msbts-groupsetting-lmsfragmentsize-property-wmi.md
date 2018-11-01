---
title: MSBTS_GroupSetting.LMSFragmentSize Property (WMI)
TOCTitle: MSBTS_GroupSetting.LMSFragmentSize Property (WMI)
ms:assetid: 04099624-c907-4fe5-ae98-17cd09559a8c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa546815(v=BTS.80)
ms:contentKeyID: 51525955
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.LMSFragmentSize Property (WMI)

 

Gets or sets the fragment size, in bytes, for large message support.

The syntax shown is language neutral.

## Syntax

``` 
  
uint32 LMSFragmentSize;  
```

## Remarks

This property is read-write.

This property is the message size below which messages will be handled in memory. Any message larger than this will be buffered to the file system to reduce memory requirements.

The default value for this property is 102400.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

