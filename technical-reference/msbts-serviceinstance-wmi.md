---
description: "Learn more about: MSBTS_ServiceInstance (WMI)"
title: MSBTS_ServiceInstance (WMI)
TOCTitle: MSBTS_ServiceInstance (WMI)
ms:assetid: b0b60759-d44b-4e2b-b8d3-3b4683564f94
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578129(v=BTS.80)
ms:contentKeyID: 51530591
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServiceInstance (WMI)

 

Provides an instance of a service, with start and stop functionality.

## Syntax

```C#
  
class MSBTS_ServiceInstance : MSBTS_BTSObject  
```

## Members

`MSBTS_ServiceInstance` defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-serviceinstance-activationtime-property-wmi.md">ActivationTime</a></td>
<td>Contains the activation time for a service instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-assemblyculture-property-wmi.md">AssemblyCulture</a></td>
<td>Contains the culture of the .NET assembly that corresponds to the service instance to which this message belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-assemblyname-property-wmi.md">AssemblyName</a></td>
<td>Contains the name of the assembly associated with the message instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-assemblypublickeytoken-property-wmi.md">AssemblyPublicKeyToken</a></td>
<td>Contains the public key token of the .NET assembly that corresponds to the service instance to which this message belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-assemblyversion-property-wmi.md">AssemblyVersion</a></td>
<td>Contains the version of the .NET assembly that corresponds to the service instance to which this message belongs.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <code>CIM_ManagedSystemElement</code><br />
<br />
)</td>
<td>For more information about the <code>CIM_ManagedSystemElement</code> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td>Description (Inherited from <code>CIM_ManagedSystemElement</code>)</td>
<td>For more information about the <code>CIM_ManagedSystemElement</code> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-errorcategory-property-wmi.md">ErrorCategory</a></td>
<td>Contains the error category when service instance is suspended.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-errordescription-property-wmi.md">ErrorDescription</a></td>
<td>Contains the error description when service instance is suspended.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-errorid-property-wmi.md">ErrorID</a></td>
<td>Contains the error code when service instance is suspended.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the host that corresponds to this queue.</td>
</tr>
<tr class="even">
<td>InstallDate (Inherited from <code>CIM_ManagedSystemElement</code>)</td>
<td>For more information about the <code>CIM_ManagedSystemElement</code> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-instanceid-property-wmi.md">InstanceID</a></td>
<td>Contains the ID of the service instance to which this message belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-msgboxdbname-property-wmi.md">MsgBoxDBName</a></td>
<td>Contains the name of the MessageBox database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-msgboxdbservername-property-wmi.md">MsgBoxDBServerName</a></td>
<td>Contains the name of the SQL Server where the MessageBox database is located.</td>
</tr>
<tr class="even">
<td>Name (Inherited from <code>CIM_ManagedSystemElement</code>)</td>
<td>For more information about the <code>CIM_ManagedSystemElement</code> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-pendingoperation-property-wmi.md">PendingOperation</a></td>
<td>Contains the type of a pending operations (if any) for this service instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-pendingoperationtime-property-wmi.md">PendingOperationTime</a></td>
<td>Contains the time of last pending operation.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-serviceclass-property-wmi.md">ServiceClass</a></td>
<td>Contains the name of the service class that corresponds to the message instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-serviceclassid-property-wmi.md">ServiceClassID</a></td>
<td>Contains the ID of the service class to which the message instance belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-servicename-property-wmi.md">ServiceName</a></td>
<td>Contains the name of the service that corresponds to the message instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-servicestatus-property-wmi.md">OrchestrationStatus</a></td>
<td>Contains the state of the service instance to which this message belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-servicetypeid-property-wmi.md">ServiceTypeID</a></td>
<td>Contains the ID of the service type to which the message instance belongs.</td>
</tr>
<tr class="even">
<td>Status (Inherited from <code>CIM_ManagedSystemElement</code>)</td>
<td>For more information about the <code>CIM_ManagedSystemElement</code> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-suspendtime-property-wmi.md">SuspendTime</a></td>
<td>Contains the time at which the service instance was suspended.</td>
</tr>
</tbody>
</table>


`MSBTS_ServiceInstance` defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-serviceinstance-resume-method-wmi.md">Resume</a></td>
<td>Enables an administrator to resume an instance of a service.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstance-suspend-method-wmi.md">Suspend</a></td>
<td>Enables an administrator to suspend an instance of a service.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-terminate-method-wmi.md">Terminate</a></td>
<td>Enables an administrator to terminate an instance of a service.</td>
</tr>
</tbody>
</table>


## Example

The following example displays how to limit the results of WMI queries on the MSBTS\_ServiceInstance and MSBTS\_MessageInstance WMI classes. These two WMI classes have support for WMI context properties that allow limiting a result set. This is required because the number of service instances or message instances may be very large. This is not the case for any other BizTalk WMI class and WMI context should be not used with them.

```C#
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

No C\# sample is provided.

## Remarks

This class may have many instances, and enumerating all of these classes may be slow and unnecessarily consume resources from the MessageBox database. If the ID of the service instance is known, use it to specify the message instance in any database lookups. For example, `select * from MSBTS_ServiceInstance where ServiceInstanceID= "GUID"`. WMI will parse the WQL to retrieve the service ID from the query and only retrieve instances that match the specified IDs.

## Requirements

Header: Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

Namespace: Included in \\root\\MicrosoftBizTalkServer.