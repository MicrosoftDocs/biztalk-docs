---
title: "MSBTS_ServiceInstance (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b0b60759-d44b-4e2b-b8d3-3b4683564f94
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstance (WMI)
Provides an instance of a service, with start and stop functionality.  
  
## Syntax  
  
```  
  
class MSBTS_ServiceInstance : MSBTS_BTSObject  
```  
  
## Members  
 `MSBTS_ServiceInstance` defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[ActivationTime](../core/msbts-serviceinstance-activationtime-property-wmi.md)|Contains the activation time for a service instance.|  
|[AssemblyCulture](../core/msbts-serviceinstance-assemblyculture-property-wmi.md)|Contains the culture of the .NET assembly that corresponds to the service instance to which this message belongs.|  
|[AssemblyName](../core/msbts-serviceinstance-assemblyname-property-wmi.md)|Contains the name of the assembly associated with the message instance.|  
|[AssemblyPublicKeyToken](../core/msbts-serviceinstance-assemblypublickeytoken-property-wmi.md)|Contains the public key token of the .NET assembly that corresponds to the service instance to which this message belongs.|  
|[AssemblyVersion](../core/msbts-serviceinstance-assemblyversion-property-wmi.md)|Contains the version of the .NET assembly that corresponds to the service instance to which this message belongs.|  
|Caption (Inherited from `CIM_ManagedSystemElement`<br /><br /> )|For more information about the `CIM_ManagedSystemElement` class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|Description (Inherited from `CIM_ManagedSystemElement`)|For more information about the `CIM_ManagedSystemElement` class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[ErrorCategory](../core/msbts-serviceinstance-errorcategory-property-wmi.md)|Contains the error category when service instance is suspended.|  
|[ErrorDescription](../core/msbts-serviceinstance-errordescription-property-wmi.md)|Contains the error description when service instance is suspended.|  
|[ErrorID](../core/msbts-serviceinstance-errorid-property-wmi.md)|Contains the error code when service instance is suspended.|  
|[HostName](../core/msbts-serviceinstance-hostname-property-wmi.md)|Contains the name of the host that corresponds to this queue.|  
|InstallDate (Inherited from `CIM_ManagedSystemElement`)|For more information about the `CIM_ManagedSystemElement` class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[InstanceID](../core/msbts-serviceinstance-instanceid-property-wmi.md)|Contains the ID of the service instance to which this message belongs.|  
|[MgmtDbNameOverride](../core/msbts-serviceinstance-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-serviceinstance-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MsgBoxDBName](../core/msbts-serviceinstance-msgboxdbname-property-wmi.md)|Contains the name of the MessageBox database.|  
|[MsgBoxDBServerName](../core/msbts-serviceinstance-msgboxdbservername-property-wmi.md)|Contains the name of the SQL Server where the MessageBox database is located.|  
|Name (Inherited from `CIM_ManagedSystemElement`)|For more information about the `CIM_ManagedSystemElement` class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[PendingOperation](../core/msbts-serviceinstance-pendingoperation-property-wmi.md)|Contains the type of a pending operations (if any) for this service instance.|  
|[PendingOperationTime](../core/msbts-serviceinstance-pendingoperationtime-property-wmi.md)|Contains the time of last pending operation.|  
|[ServiceClass](../core/msbts-serviceinstance-serviceclass-property-wmi.md)|Contains the name of the service class that corresponds to the message instance.|  
|[ServiceClassID](../core/msbts-serviceinstance-serviceclassid-property-wmi.md)|Contains the ID of the service class to which the message instance belongs.|  
|[ServiceName](../core/msbts-serviceinstance-servicename-property-wmi.md)|Contains the name of the service that corresponds to the message instance.|  
|[OrchestrationStatus](../core/msbts-serviceinstance-servicestatus-property-wmi.md)|Contains the state of the service instance to which this message belongs.|  
|[ServiceTypeID](../core/msbts-serviceinstance-servicetypeid-property-wmi.md)|Contains the ID of the service type to which the message instance belongs.|  
|Status (Inherited from `CIM_ManagedSystemElement`)|For more information about the `CIM_ManagedSystemElement` class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[SuspendTime](../core/msbts-serviceinstance-suspendtime-property-wmi.md)|Contains the time at which the service instance was suspended.|  
  
 `MSBTS_ServiceInstance` defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[Resume](../core/msbts-serviceinstance-resume-method-wmi.md)|Enables an administrator to resume an instance of a service.|  
|[Suspend](../core/msbts-serviceinstance-suspend-method-wmi.md)|Enables an administrator to suspend an instance of a service.|  
|[Terminate](../core/msbts-serviceinstance-terminate-method-wmi.md)|Enables an administrator to terminate an instance of a service.|  
  
## Example  
 The following example displays how to limit the results of WMI queries on the MSBTS_ServiceInstance and MSBTS_MessageInstance WMI classes. These two WMI classes have support for WMI context properties that allow limiting a result set. This is required because the number of service instances or message instances may be very large. This is not the case for any other BizTalk WMI class and WMI context should be not used with them.  
  
```  
EnumAllInstances  
  
If Err <> 0 Then  
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
  
Sub PrintWMIErrorThenExit(strErrDesc, ErrNum)  
 On Error Resume Next  
 Dim objWMIError : Set objWMIError = CreateObject("WbemScripting.SwbemLastError")  
  
 If ( TypeName(objWMIError) = "Empty" ) Then  
wscript.echo strErrDesc & " (HRESULT: " & Hex(ErrNum) & ")."  
 Else  
wscript.echo objWMIError.Description & "(HRESULT: " & Hex(ErrNum) & ")."  
Set objWMIError = nothing  
 End If  
End Sub  
```  
  
 No C# sample is provided.  
  
## Remarks  
 This class may have many instances, and enumerating all of these classes may be slow and unnecessarily consume resources from the MessageBox database. If the ID of the service instance is known, use it to specify the message instance in any database lookups. For example, `select * from MSBTS_ServiceInstance where ServiceInstanceID= "GUID"`. WMI will parse the WQL to retrieve the service ID from the query and only retrieve instances that match the specified IDs.  
  
## Requirements  
 Header: Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 Namespace: Included in \root\MicrosoftBizTalkServer.