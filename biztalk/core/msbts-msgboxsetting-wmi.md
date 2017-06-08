---
title: "MSBTS_MsgBoxSetting (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4e245bf-a643-4367-a165-fb34872fa19a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MsgBoxSetting (WMI)
Represents a single MessageBox setting in the Microsoft BizTalk Server group.  
  
## Declaration  
  
```  
class MSBTS_MsgBoxSetting : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_MsgBoxSetting** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[DisableNewMessagePublication](../core/msbts-msgboxsetting-disablenewmessagepublication-property-wmi.md)|Enables or disables the publication of new messages in the MessageBox setting.|  
|[IsMasterMsgBox](../core/msbts-msgboxsetting-ismastermsgbox-property-wmi.md)|Indicates whether this MessageBox is the master MessageBox.|  
|[MgmtDbNameOverride](../core/msbts-msgboxsetting-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connection string. **Note:**  The BizTalk Management database is also referred to as the BizTalk Configuration database.|  
|[MgmtDbServerOverride](../core/msbts-msgboxsetting-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MsgBoxDBName](../core/msbts-msgboxsetting-msgboxdbname-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MsgBoxDBServerName](../core/msbts-msgboxsetting-msgboxdbservername-property-wmi.md)|Contains the name of the SQL Server where the MessageBox setting database is located.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
  
 **MSBTS_MsgBoxSetting** defines the following method:  
  
|Method|Description|  
|------------|-----------------|  
|[ForceDelete](../core/msbts-msgboxsetting-forcedelete-method-wmi.md)|Deletes the MessageBox object.|  
  
## Remarks  
 For more information about the minimum security user rights required to administer the MessageBox database, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.