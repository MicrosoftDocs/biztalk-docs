---
title: "MSBTS_MessageInstance (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e85b0e3-5e92-403c-a8bf-c5d6b5f30f10
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MessageInstance (WMI)
Represents a message instance.  
  
## Declaration  
  
```  
class MSBTS_MessageInstance : MSBTS_BTSObject  
```  
  
## Members  
 **MSBTS_MessageInstance** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[AssemblyCulture](../core/msbts-messageinstance-assemblyculture-property-wmi.md)|Contains the culture of the .NET assembly that corresponds to the service instance to which this message belongs.|  
|[AssemblyName](../core/msbts-messageinstance-assemblyname-property-wmi.md)|Contains the name of the assembly associated with the message instance.|  
|[AssemblyPublicKeyToken](../core/msbts-messageinstance-assemblypublickeytoken-property-wmi.md)|Contains the public key token of the .NET assembly that corresponds to the service instance to which this message belongs.|  
|[AssemblyVersion](../core/msbts-messageinstance-assemblyversion-property-wmi.md)|Contains the version of the .NET assembly that corresponds to the service instance to which this message belongs.|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[Context](../core/msbts-messageinstance-context-property-wmi.md)|Contains the message context.|  
|[CreationTime](../core/msbts-messageinstance-creationtime-property-wmi.md)|Contains the time that this message was last modified.|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[HostName](../core/msbts-messageinstance-hostname-property-wmi.md)|Contains the name of the host that corresponds to this queue.|  
|[InboundAdapterName](../core/msbts-messageinstance-inboundadaptername-property-wmi.md)|Contains the name of the adapter that received this message.|  
|[InboundURL](../core/msbts-messageinstance-inboundurl-property-wmi.md)|Contains the name of the URL this message is received from.|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[MessageInstanceID](../core/msbts-messageinstance-messageinstanceid-property-wmi.md)|Contains the ID of the message instance.|  
|[MessageType](../core/msbts-messageinstance-messagetype-property-wmi.md)|Contains the document type that corresponds to this message.|  
|[MgmtDbNameOverride](../core/msbts-messageinstance-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-messageinstance-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MsgBoxDBName](../core/msbts-messageinstance-msgboxdbname-property-wmi.md)|Contains the name of the MessageBox database.|  
|[MsgBoxDBServerName](../core/msbts-messageinstance-msgboxdbservername-property-wmi.md)|Contains the name of the SQL Server where the MessageBox database is located.|  
|Name (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[OriginatorPID](../core/msbts-messageinstance-originatorpid-property-wmi.md)|Contains the originators PID.|  
|[OriginatorSID](../core/msbts-messageinstance-originatorsid-property-wmi.md)|Contains the originators SID.|  
|[OutboundAdapterName](../core/msbts-messageinstance-outboundadaptername-property-wmi.md)|Contains the name of the adapter that will send this message.|  
|[OutboundURL](../core/msbts-messageinstance-outboundurl-property-wmi.md)|Contains the name of the URL this message is going to be sent to.|  
|[PublisherLogon](../core/msbts-messageinstance-publisherlogon-property-wmi.md)|Contains logon of the BizTalk Host instance that created the message.|  
|[ReferenceType](../core/msbts-messageinstance-referencetype-property-wmi.md)|Contains information about how message is referenced by a service.|  
|[RetryCount](../core/msbts-messageinstance-retrycount-property-wmi.md)|Contains the number of attempts made to send this message.|  
|[SendPortName](../core/msbts-messageinstance-sendportname-property-wmi.md)|Contains the name of the send port that this message is going to be sent through.|  
|[ServiceClass](../core/msbts-messageinstance-serviceclass-property-wmi.md)|Contains the name of the service class that corresponds to the message instance.|  
|[ServiceClassID](../core/msbts-messageinstance-serviceclassid-property-wmi.md)|Contains the ID of the service class to which the message instance belongs.|  
|[ServiceInstanceID](../core/msbts-messageinstance-serviceinstanceid-property-wmi.md)|Contains the ID of the service instance to which the message instance belongs.|  
|[ServiceInstanceStatus](../core/msbts-messageinstance-serviceinstancestatus-property-wmi.md)|Contains state of the service instance to which this message belongs.|  
|[ServiceName](../core/msbts-messageinstance-servicename-property-wmi.md)|Contains the name of the service that corresponds to the message instance.|  
|[ServiceTypeID](../core/msbts-messageinstance-servicetypeid-property-wmi.md)|Contains the ID of the service type to which the message instance belongs.|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
  
 **MSBTS_MessageInstance** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[SaveToFile](../core/msbts-messageinstance-savetofile-method-wmi.md)|Enables an administrator to save message context and parts into multiple output files.|  
  
## Example  
 The following example displays how to limit the results of WMI queries on the MSBTS_ServiceInstance and MSBTS_MessageInstance WMI classes. These two WMI classes have support for WMI context properties that allow limiting a result set. This is required because the number of service instances or message instances may be very large. This is not the case for any other BizTalk WMI class and WMI context should be not used with them.  
  
```vb  
EnumAllInstances  
  
If Err <> 0   Then  
   PrintWMIErrorThenExit Err.Description, Err.Number  
End If  
  
Sub EnumAllInstances  
   Dim Context, FromTime, UntilTime, InstSet, Query  
  
   wbemFlagReturnImmediately = 16 '0x10  
   Set Context = CreateObject("WbemScripting.SWbemNamedValueSet")  
   Set FromTime = CreateObject("WbemScripting.SWbemDateTime")  
   Set UntilTime = CreateObject("WbemScripting.SWbemDateTime")  
  
   FromTime.Year = 2003  
   UntilTime.Year = 2003  
   UntilTime.Month = 3  
   UntilTime.Day = 26  
   UntilTime.Hours = 19  
   UntilTime.Minutes = 32  
  
   Context.Add "From", FromTime.Value  
   Context.Add "Until", UntilTime.Value  
   Context.Add "IterationDelayMS", 10  
  
   Query = "SELECT * FROM MSBTS_ServiceInstance"  
  
   Set InstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(Query, "WQL", wbemFlagReturnImmediately, Context)  
   If Err <> 0 Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   For Each Inst In InstSet  
      wscript.echo Inst.InstanceID + " " + Inst.HostName  
   Next  
  
End Sub  
  
Sub   PrintWMIErrorThenExit(strErrDesc, ErrNum)  
   On Error Resume Next  
   Dim   objWMIError : Set objWMIError =   CreateObject("WbemScripting.SwbemLastError")  
  
   If ( TypeName(objWMIError) = "Empty" ) Then  
      wscript.echo strErrDesc & " (HRESULT: " & Hex(ErrNum) & ")."  
   Else  
      wscript.echo objWMIError.Description & "(HRESULT: "     & Hex(ErrNum) & ")."  
      Set objWMIError = nothing  
   End     If  
End     Sub  
```  
  
 No C# sample is provided.  
  
## Remarks  
 This class may have many instances, and enumerating all of these classes may be slow and unnecessarily consume resources from the MessageBox database. If the ID of the message instance is known, use it to specify the message instance in any database lookups. For example, `select * from MSBTS_MessageInstance where MessageInstanceID= "GUID"`. WMI will parse the WQL to retrieve the message ID from the query and only retrieve instances that match the specified IDs.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.