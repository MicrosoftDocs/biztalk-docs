---
title: "Core Server Classes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e1f87e1-6c20-459b-89d9-b478c7353a8d
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Core Server Classes
The Windows Management Instrumentation (WMI) classes in this table are used to manage the core objects associated with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], such as servers, queues, groups, and message handlers.  
  
 To view core server class and member information in CIM Studio, see [Viewing the WMI Core Server Classes in CIM Studio](../core/viewing-the-wmi-core-server-classes-in-cim-studio.md). You can also view the MOF file and the member descriptions in a text editor, however the descriptions are easier to read in  CIM Studio.  
  
 WMI Samples are available in the Examples section and in the SDK and in this section. For more information, see [WMI Script Samples](../core/wmi-script-samples.md) and [Admin\WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md).  
  
> [!WARNING]
>  If your BizTalk Configuration database is using a non-binary, case-sensitive collation then you must enter parameter values for object names and other key values in the correct case. For example, if a Send Port is configured with the name "SendPort" and you are using a non-binary, case-sensitive collation, you must enter "SendPort" as the name when working with WMI or calls will fail.  
  
|Class|Description|  
|-----------|-----------------|  
|[MSBTS_AdapterSetting](../core/msbts-adaptersetting-wmi.md)|Registers new adapters with Microsoft® BizTalk® Server.|  
|[MSBTS_BTSObject](../core/msbts-btsobject-wmi.md)|This type or member supports the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure and is not intended to be used directly from your code.|  
|[MSBTS_DeploymentService](../core/msbts-deploymentservice-wmi.md)|Encapsulates BizTalk assemblies for deployment or undeployment and bindings export or import.|  
|[MSBTS_GroupSetting](../core/msbts-groupsetting-wmi.md)|Represents a logical grouping of BizTalk Servers.|  
|[MSBTS_Host](../core/msbts-host-wmi.md)|Represents a BizTalk Server Host.|  
|[MSBTS_HostInstance](../core/msbts-hostinstance-wmi.md)|Represents a single instance of a BizTalk Host.|  
|[MSBTS_HostInstanceSetting](../core/msbts-hostinstancesetting-wmi.md)|Updates the [IsDisabled](../core/msbts-hostinstancesetting-isdisabled-property-wmi.md) property when a host is in the stopped state.|  
|[MSBTS_HostQueue](../core/msbts-hostqueue-wmi.md)|Represents an application.|  
|[MSBTS_HostSetting](../core/msbts-hostsetting-wmi.md)|Creates a BizTalk Server Host setting.|  
|[MSBTS_MessageInstance](../core/msbts-messageinstance-wmi.md)|Represents a message instance.|  
|[MSBTS_MessageInstanceSuspendedEvent](../core/msbts-messageinstancesuspendedevent-wmi.md)|Represents a suspended event for a BizTalk Message Queuing (MSMQT) message instance.|  
|[MSBTS_MsgBoxSetting](../core/msbts-msgboxsetting-wmi.md)|Represents a single MessageBox setting in the BizTalk Server group.|  
|[MSBTS_Orchestration](../core/msbts-orchestration-wmi.md)|Represents an instance of an orchestration that belongs to the installed module.|  
|[MSBTS_ReceiveHandler](../core/msbts-receivehandler-wmi.md)|Represents an individual receive handler defined by BizTalk Server.|  
|[MSBTS_ReceiveLocation](../core/msbts-receivelocation-wmi.md)|Represents an individual receive location defined by BizTalk Server.|  
|[MSBTS_ReceiveLocationOrchestration](../core/msbts-receivelocationorchestration-wmi.md)|Represents all possible combinations of receive locations and orchestrations.|  
|[MSBTS_ReceivePort](../core/msbts-receiveport-wmi.md)|Represents an individual receive port defined by BizTalk Server.|  
|[MSBTS_SendHandler](../core/msbts-sendhandler-wmi.md)|Represents an individual send handler defined by BizTalk Server.|  
|[MSBTS_SendHandler2](../core/msbts-sendhandler2-wmi.md)|Represents an extended individual send handler defined by BizTalk Server.|  
|[MSBTS_SendPort](../core/msbts-sendport-wmi.md)|Represents an individual send port defined by BizTalk Server.|  
|[MSBTS_SendPortGroup](../core/msbts-sendportgroup-wmi.md)|Represents group of send ports defined by the BizTalk Server.|  
|[MSBTS_SendPortGroup2SendPort (WMI)](../core/msbts-sendportgroup2sendport-wmi.md)|Represents an extended group of send ports defined by the BizTalk Server.|  
|[MSBTS_Server](../core/msbts-server-wmi.md)|Represents computers within a group that have BizTalk Servers installed.|  
|[MSBTS_ServerHost](../core/msbts-serverhost-wmi.md)|Reflects mappings between BizTalk servers and BizTalk Hosts.|  
|[MSBTS_ServerSetting](../core/msbts-serversetting-wmi.md)|Represents specific computers within the BizTalk group that have BizTalk Servers installed. Instances of this class are intended to be created and deleted internally through BizTalk Server only. Do not create or delete instance of this class explicitly through WMI.|  
|[MSBTS_Service](../core/msbts-service-wmi.md)|This type or member supports the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure and is not intended to be used directly from your code.|  
|[MSBTS_ServiceInstance](../core/msbts-serviceinstance-wmi.md)|Provides an instance of a service, with start and stop functionality.|  
|[MSBTS_ServiceInstanceSuspendedEvent](../core/msbts-serviceinstancesuspendedevent-wmi.md)|Represents a suspended event for a service instance.|  
|[MSBTS_Setting](../core/msbts-setting-wmi.md)|This type or member supports the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure and is not intended to be used directly from your code.|  
|[MSBTS_TrackedMessageInstance](../core/msbts-trackedmessageinstance-wmi.md)|Represents a message instance.|  
|[MSBTS_TrackedMessageInstance2 (WMI)](../core/msbts-trackedmessageinstance2-wmi.md)|Represents an updated message instance.|  
  
 **Remarks**  
  
 For more information about the minimum security user rights required to administer items using WMI, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).