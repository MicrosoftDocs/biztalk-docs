---
title: "WmiSnaStatus WMI Provider Classes1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e17d9658-eff3-4cba-995d-9b1d855b113d
caps.latest.revision: 4
---
# WmiSnaStatus WMI Provider Classes
The Microsoft® Host Integration Server SNA Status provider supplies information regarding the SNA service status. As an instance and method provider, the WmiSnaStatus provider implements the standard **IWbemProviderInit** interface and the following **IWbemServices** methods:  
  
 **CreateInstanceEnumAsync**  
  
 **DeleteInstanceAsync**  
  
 **ExecMethodAsync**  
  
 **ExecQueryAsync**  
  
 **GetObjectAsync**  
  
 **PutInstanceAsync**  
  
 For more information on **IWbemProviderInit** and **IWbemServices**, see "COM API for WMI" in the MSDN Library at http://msdn.microsoft.com/library.  
  
 The WmiSnaStatus.mof and WmiSnaStatus_XP file contains the WMISNA provider, and association and registration classes. You can access these provider classes in the \root\MicrosoftHIS namespace.  
  
|Class|Description|  
|-----------|-----------------|  
|[MsSnaStatus_EventServiceSna](../core/mssnastatus-eventservicesna-class.md)|Describes a change to the **EventServiceSna** class.|  
|[MsSnaStatus_EventConnection](../core/mssnastatus-eventconnection-class.md)|Describes a change to the **EventConnection** class|  
|[MsSnaStatus_EventLu3270](../core/mssnastatus-eventlu3270-class.md)|Describes a change to the **EventLu3270** class.|  
|[MsSnaStatus_EventUser](../core/mssnastatus-eventuser-class.md)|Describes a change to the **EventUser** class.|  
|[MsSnaStatus_EventAppcLocalLu](../core/mssnastatus-eventappclocallu-class.md)|Describes a change to the **EventAppcLocalLu** class.|  
|[MsSnaStatus_EventAppcSession](../core/mssnastatus-eventappcsession-class.md)|Describes a change to the **EventAppcSession** class.|  
|[MsSnaStatus_EventServicePrint](../core/mssnastatus-eventserviceprint-class.md)|Describes a change to the **EventServicePrint** class.|  
|[MsSnaStatus_EventPrintSession](../core/mssnastatus-eventprintsession-class.md)|Describes a change to the **EventPrintSession** class.|  
|[MsSnaStatus_EventServiceTN3270](../core/mssnastatus-eventservicetn3270-class.md)|Describes a change to the **EventServiceTN3270** class.|  
|[MsSnaStatus_EventTN3270Session](../core/mssnastatus-eventtn3270session-class.md)|Describes a change to the **EventTN3270Session** class.|  
|[MsSnaStatus_EventServiceTN5250](../core/mssnastatus-eventservicetn5250-class.md)|Describes a change to the **EventTN5250Session** class.|  
|[MsSnaStatus_EventServiceSharedFolder](../core/mssnastatus-eventservicesharedfolder-class.md)|Describes a change to the **EventServiceSharedFolder** class.|  
|[SNA_ExtendedStatus](../core/sna-extendedstatus-class.md)|Used to return error information if required.|  
|[MsSnaStatus_ServiceSna](../core/mssnastatus-servicesna-class.md)|Get information on the status of the SNA service.|  
|[MsSnaStatus_Connection](../core/mssnastatus-connection-class.md)|Represents a SNA Service connection status.|  
|[MsSnaStatus_Lu3270](../core/mssnastatus-lu3270-class.md)|Represents a SNA Service display LU, printer LU, or LUA LU status.|  
|[MsSnaStatus_ClientConnections](../core/mssnastatus-clientconnections-class.md)|Represents a SNA Service client connection status.|  
|[MsSnaStatus_AppcLocalLu](../core/mssnastatus-appclocallu-class.md)|Represents an APPC Local LU status.|  
|[MsSnaStatus_AppcSession](../core/mssnastatus-appcsession-class.md)|Represents an APPC session status.|  
|[MsSnaStatus_ServicePrint](../core/mssnastatus-serviceprint-class.md)|Represents an Host Printer service status.|  
|[MsSnaStatus_PrintSession](../core/mssnastatus-printsession-class.md)|Represents an Host Printer session status.|  
|[MsSnaStatus_ServiceTN3270](../core/mssnastatus-servicetn3270-class.md)|Represents a TN3270 service status.|  
|[MsSnaStatus_TN3270Session](../core/mssnastatus-tn3270session-class.md)|Represents a TN3270 session status.|  
|[MsSnaStatus_ServiceTN5250](../core/mssnastatus-servicetn5250-class.md)|Represents a TN5250 service status.|  
|[MsSnaStatus_TN5250Session](../core/mssnastatus-tn5250session-class.md)|Represents a TN5250 session status.|  
|[MsSnaStatus_ServiceSharedFolder](../core/mssnastatus-servicesharedfolder-class.md)|Represents a TN3270 service status.|  
|[MsSnaStatus_Lu3270ToActiveUser](../core/mssnastatus-lu3270toactiveuser-class.md)|Represents an association between a User connection and a 3270 type LU.|  
|[MsSnaStatus_APPCSessionToActiveUser](../core/mssnastatus-appcsessiontoactiveuser-class.md)|Represents an association between a User connection and an APPC session.|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012