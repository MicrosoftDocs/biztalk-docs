---
title: MSBTS_MsgBoxSetting.MsgBoxDBServerName Property (WMI)
TOCTitle: MSBTS_MsgBoxSetting.MsgBoxDBServerName Property (WMI)
ms:assetid: 8573cbc4-a5dc-4ec8-87fa-37b35034d6f1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561176(v=BTS.80)
ms:contentKeyID: 51529412
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MsgBoxSetting.MsgBoxDBServerName Property (WMI)

 

Contains the name of the SQL Server where the MessageBox database is located.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MsgBoxDBServerName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **MsgBoxDBName**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

