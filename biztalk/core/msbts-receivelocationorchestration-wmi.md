---
title: "MSBTS_ReceiveLocationOrchestration (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0835f43a-25ce-431d-b4ba-a1f7105d9047
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocationOrchestration (WMI)
Represents all possible combinations of receive locations and orchestrations.  
  
## Declaration  
  
```  
class MSBTS_ReceiveLocationOrchestration : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_ReceiveLocationOrchestration** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[AdapterName](../core/msbts-receivelocationorchestration-adaptername-property-wmi.md)|Contains the name of the adapter used by the given instance of the receive location.|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[InboundTransportUrl](../core/msbts-receivelocationorchestration-inboundtransporturl-property-wmi.md)|Contains the URL provided by the transport component, based on the specific adapter configuration.|  
|[IsDisabled](../core/msbts-receivelocationorchestration-isdisabled-property-wmi.md)|Enables or disables a receive location.|  
|[IsPrimary](../core/msbts-receivelocationorchestration-isprimary-property-wmi.md)|Specifies a primary receive location to use for correlation.|  
|[MgmtDbNameOverride](../core/msbts-receivelocationorchestration-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-receivelocationorchestration-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[OrchestrationAssemblyCulture](../core/msbts-receivelocationorchestration-orchestrationassemblyculture-property-wmi.md)|Contains the culture of the Microsoft® .NET-based assembly with which this orchestration belongs.|  
|[OrchestrationAssemblyName](../core/msbts-receivelocationorchestration-orchestrationassemblyname-property-wmi.md)|Contains the name of the Microsoft® .NET-based assembly to which this orchestration belongs.|  
|[OrchestrationAssemblyPublicKeyToken](../core/msbts_receivelocationorchestration-orchestrationassemblypublickeytoken-wmi-.md)|Contains the public key token of the Microsoft® .NET-based assembly with which this orchestration belongs.|  
|[OrchestrationAssemblyVersion](../core/msbts-receivelocationorchestration-orchestrationassemblyversion-property-wmi.md)|Contains the version of the Microsoft® .NET-based assembly with which this orchestration belongs.|  
|[OrchestrationHostName](../core/msbts-receivelocationorchestration-orchestrationhostname-property-wmi.md)|Contains the name of the BizTalk host with which this orchestration is enlisted.|  
|[OrchestrationName](../core/msbts-receivelocationorchestration-orchestrationname-property-wmi.md)|Contains the host name with which this orchestration is enlisted.|  
|[OrchestrationStatus](../core/msbts-receivelocationorchestration-orchestrationstatus-property-wmi.md)|Indicates the status of the orchestration.|  
|[PipelineName](../core/msbts-receivelocationorchestration-pipelinename-property-wmi.md)|Represents the name of the pipeline that will process the document before it is submitted to the MessageBox.|  
|[ReceiveHostName](../core/msbts-receivelocationorchestration-receivehostname-property-wmi.md)|Contains the name of the BizTalk Host for the receive handler hosting the given instance of the receive location.|  
|[ReceiveLocationName](../core/msbts-receivelocationorchestration-receivelocationname-property-wmi.md)|Contains the name of the receive location.|  
|[ReceivePortName](../core/msbts-receivelocationorchestration-receiveportname-property-wmi.md)|Contains the name of receive port used by the given instance of the receive location.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.