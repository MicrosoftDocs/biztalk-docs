---
title: MSBTS_MsgBoxSetting.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_MsgBoxSetting.MgmtDbServerOverride Property (WMI)
ms:assetid: 6711c16c-94c2-4d26-9908-02174ac5671a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560556(v=BTS.80)
ms:contentKeyID: 51528582
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MsgBoxSetting.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MsgBoxDBName**, and **MsgBoxDBServerName**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

