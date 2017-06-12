---
title: "MSBTS_SendPortGroup (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38ba51dd-d332-4300-9bc4-2eb1bbbc57a7
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPortGroup (WMI)
Represents group of send ports defined by the BizTalk Server.  
  
## Declaration  
  
```  
class MSBTS_SendPortGroup : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_SendPortGroup** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at http://go.microsoft.com/fwlink/p/?LinkID=20246.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at http://go.microsoft.com/fwlink/p/?LinkID=20246.|  
|[Filter](../core/msbts-sendportgroup-filter-property-wmi.md)|Contains textual representation of the filter.|  
|[MgmtDbNameOverride](../core/msbts-sendportgroup-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-sendportgroup-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-sendportgroup-name-property-wmi.md)|Contains the name of the send port group.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at http://go.microsoft.com/fwlink/p/?LinkID=20246.|  
|[Status](../core/msbts-sendportgroup-status-property-wmi.md)|Displays the current status of the port.|  
  
 **MSBTS_SendPortGroup** defines the following methods:  
  
|Property|Description|  
|--------------|-----------------|  
|[Enlist](../core/msbts-sendportgroup-enlist-method-wmi.md)|Enlists the send port group.|  
|[Start](../core/msbts-sendportgroup-start-method-wmi.md)|Starts the send port group.|  
|[Stop](../core/msbts-sendportgroup-stop-method-wmi.md)|Stops the send port group.|  
|[UnEnlist](../core/msbts-sendportgroup-unenlist-method-wmi.md)|Unenlists the send port group.|  
  
## Remarks  
 The **MSBTS_SendPortGroup** class operates differently than the user interface to add a send port group using BizTalk Explorer. In BizTalk Explorer, you cannot create a send port group that contains no send ports. Using the **MSBTS_SendPortGroup** class, you must create an empty group first, and then use the MSBTS**_SendPortGroup2SendPort** class to add send ports to the group.  
  
> [!NOTE]
>  If you create a send port group that contains no send ports, BizTalk Explorer will raise an error when the group is clicked. To avoid this, ensure that any send port groups you create contain at least one port.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPortGroup** class.   
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.