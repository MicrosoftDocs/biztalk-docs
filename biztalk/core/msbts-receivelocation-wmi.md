---
title: "MSBTS_ReceiveLocation (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f75bd1ce-1bf5-4707-9b8e-55377c2538a1
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation (WMI)
Represents an individual receive location defined by Microsoft BizTalk Server.  
  
> [!WARNING]
>  Certificates must be installed on the box for the MSBTS_ReceiveLocation class to work. The only way to create receive locations without certificates is to use the  [Microsoft.BizTalk.ExplorerOM](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx)APIs.  
  
## Declaration  
  
```  
class MSBTS_ReceiveLocation : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_ReceiveLocation** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[MSBTS_ReceiveLocation.ActiveStartDT Property (WMI)](../core/msbts-receivelocation-activestartdt-property-wmi.md)|Contains the date when the receive location should activate.|  
|[MSBTS_ReceiveLocation.ActiveStopDT Property (WMI)](../core/msbts-receivelocation-activestopdt-property-wmi.md)|Contains the date when the receive location should deactivate.|  
|[MSBTS_ReceiveLocation.AdapterName Property (WMI)](../core/msbts-receivelocation-adaptername-property-wmi.md)|Contains the name of the adapter used by the receive location.|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/p/?LinkID=20246](http://go.microsoft.com/fwlink/p/?LinkID=20246).|  
|[MSBTS_ReceiveLocation.CustomCfg Property (WMI)](../core/msbts-receivelocation-customcfg-property-wmi.md)|Contains the adapter-specific configuration in XML format.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/p/?LinkID=20246](http://go.microsoft.com/fwlink/p/?LinkID=20246).|  
|[MSBTS_ReceiveLocation.EncryptionCert (WMI)](../core/msbts-receivelocation-encryptioncert-wmi.md)|Contains the Name of the certificate used for outbound encryption.|  
|[MSBTS_ReceiveLocation.HostName Property (WMI)](../core/msbts-receivelocation-hostname-property-wmi.md)|Contains the name of the receive handler used by the receive location.|  
|[MSBTS_ReceiveLocation.InboundAddressableURL Property (WMI)](../core/msbts-receivelocation-inboundaddressableurl-property-wmi.md)|Contains a URL that can be used by external parties to send documents to the receive location.|  
|[MSBTS_ReceiveLocation.InboundTransportURL Property (WMI)](../core/msbts-receivelocation-inboundtransporturl-property-wmi.md)|Contains an adapter-specific URL which the given instance of the receive location is listening to.|  
|[MSBTS_ReceiveLocation.IsDisabled Property (WMI)](../core/msbts-receivelocation-isdisabled-property-wmi.md)|Enables or disables a receive function.|  
|[MSBTS_ReceiveLocation.IsPrimary Property (WMI)](../core/msbts-receivelocation-isprimary-property-wmi.md)|Specifies a primary receive function to use for correlation.|  
|[MSBTS_ReceiveLocation.MgmtDbNameOverride Property (WMI)](../core/msbts-receivelocation-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and is reserved for future use.|  
|[MSBTS_ReceiveLocation.MgmtDbServerOverride Property (WMI)](../core/msbts-receivelocation-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and is reserved for future use.|  
|[MSBTS_ReceiveLocation.Name Property (WMI)](../core/msbts-receivelocation-name-property-wmi.md)|Contains the name of the receive location.|  
|[MSBTS_ReceiveLocation.OperatingWindowEnabled (WMI)](../core/msbts-receivelocation-operatingwindowenabled-wmi.md)|Enables or disables a service window, which is defined by the **SrvWinStartDT** and **SrvWinStopDT** properties.|  
|[MSBTS_ReceiveLocation.PipelineName Property (WMI)](../core/msbts-receivelocation-pipelinename-property-wmi.md)|Contains the name of the pipeline that will process the document before the document is submitted to the MessageBox database.|  
|[MSBTS_ReceiveLocation.ReceivePortName Property (WMI)](../core/msbts-receivelocation-receiveportname-property-wmi.md)|Contains the name of the receive port used by the receive location.|  
|[MSBTS_ReceiveLocation.SendPipeline (WMI)](../core/msbts-receivelocation-sendpipeline-wmi.md)|Contains the name of the send pipeline used by the receive location.|  
|[MSBTS_ReceiveLocation.SendPipelineData (WMI)](../core/msbts-receivelocation-sendpipelinedata-wmi.md)|Contains the custom configuration data for the SendPipeline in XML format.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/p/?LinkID=20246](http://go.microsoft.com/fwlink/p/?LinkID=20246).|  
|[MSBTS_ReceiveLocation.SrvWinStartDT Property (WMI)](../core/msbts-receivelocation-srvwinstartdt-property-wmi.md)|Contains the start time of a service window when the receive location should activate.|  
|[MSBTS_ReceiveLocation.SrvWinStopDT Property (WMI)](../core/msbts-receivelocation-srvwinstopdt-property-wmi.md)|Contains the end time of a service window when the receive location should deactivate.|  
|[MSBTS_ReceiveLocation.StartDateEnabled (WMI)](../core/msbts-receivelocation-startdateenabled-wmi.md)|Enables or disables the active start date specified by **ActiveStartDT** property.|  
|[MSBTS_ReceiveLocation.StopDateEnabled (WMI)](../core/msbts-receivelocation-stopdateenabled-wmi.md)|Enables or disables the active stop date specified by **ActiveStopDT** property.|  
  
 **MSBTS_ReceiveLocation** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[MSBTS_ReceiveLocation.Disable Method (WMI)](../core/msbts-receivelocation-disable-method-wmi.md)|Disables a receive location.|  
|[MSBTS_ReceiveLocation.Enable Method (WMI)](../core/msbts-receivelocation-enable-method-wmi.md)|Enables a receive location.|  
  
## Remarks  
  
> [!NOTE]
>  If a send port or receive location is updated using the BizTalk Explorer object model or a WMI script, the Receive Port Properties and Send Port Properties property pages in BizTalk Explorer will display an incorrect Address (URI). The Address (URI) used internally is the Address (URI) set by the script, so the script works as expected. To update the property pages to display the correct Address (URI), update the Address (URI) field in BizTalk Explorer with the new value.  
  
> [!NOTE]
>  This class wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceiveLocation** class.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.