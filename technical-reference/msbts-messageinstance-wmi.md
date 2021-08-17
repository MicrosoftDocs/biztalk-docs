---
description: "Learn more about: MSBTS_MessageInstance (WMI)"
title: MSBTS_MessageInstance (WMI)
TOCTitle: MSBTS_MessageInstance (WMI)
ms:assetid: 1e85b0e3-5e92-403c-a8bf-c5d6b5f30f10
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559119(v=BTS.80)
ms:contentKeyID: 51526687
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_MessageInstance (WMI)

 

Represents a message instance.

## Declaration

```C#
class MSBTS_MessageInstance : MSBTS_BTSObject  
```

## Members

**MSBTS\_MessageInstance** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-messageinstance-assemblyculture-property-wmi.md">AssemblyCulture</a></td>
<td>Contains the culture of the .NET assembly that corresponds to the service instance to which this message belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-assemblyname-property-wmi.md">AssemblyName</a></td>
<td>Contains the name of the assembly associated with the message instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-assemblypublickeytoken-property-wmi.md">AssemblyPublicKeyToken</a></td>
<td>Contains the public key token of the .NET assembly that corresponds to the service instance to which this message belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-assemblyversion-property-wmi.md">AssemblyVersion</a></td>
<td>Contains the version of the .NET assembly that corresponds to the service instance to which this message belongs.</td>
</tr>
<tr class="odd">
<td>Caption (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-context-property-wmi.md">Context</a></td>
<td>Contains the message context.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-creationtime-property-wmi.md">CreationTime</a></td>
<td>Contains the time that this message was last modified.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the host that corresponds to this queue.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-inboundadaptername-property-wmi.md">InboundAdapterName</a></td>
<td>Contains the name of the adapter that received this message.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-inboundurl-property-wmi.md">InboundURL</a></td>
<td>Contains the name of the URL this message is received from.</td>
</tr>
<tr class="even">
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-messageinstanceid-property-wmi.md">MessageInstanceID</a></td>
<td>Contains the ID of the message instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-messagetype-property-wmi.md">MessageType</a></td>
<td>Contains the document type that corresponds to this message.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-msgboxdbname-property-wmi.md">MsgBoxDBName</a></td>
<td>Contains the name of the MessageBox database.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-msgboxdbservername-property-wmi.md">MsgBoxDBServerName</a></td>
<td>Contains the name of the SQL Server where the MessageBox database is located.</td>
</tr>
<tr class="odd">
<td>Name (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-originatorpid-property-wmi.md">OriginatorPID</a></td>
<td>Contains the originators PID.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-originatorsid-property-wmi.md">OriginatorSID</a></td>
<td>Contains the originators SID.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-outboundadaptername-property-wmi.md">OutboundAdapterName</a></td>
<td>Contains the name of the adapter that will send this message.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-outboundurl-property-wmi.md">OutboundURL</a></td>
<td>Contains the name of the URL this message is going to be sent to.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-publisherlogon-property-wmi.md">PublisherLogon</a></td>
<td>Contains logon of the BizTalk Host instance that created the message.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-referencetype-property-wmi.md">ReferenceType</a></td>
<td>Contains information about how message is referenced by a service.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-retrycount-property-wmi.md">RetryCount</a></td>
<td>Contains the number of attempts made to send this message.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-sendportname-property-wmi.md">SendPortName</a></td>
<td>Contains the name of the send port that this message is going to be sent through.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-serviceclass-property-wmi.md">ServiceClass</a></td>
<td>Contains the name of the service class that corresponds to the message instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-serviceclassid-property-wmi.md">ServiceClassID</a></td>
<td>Contains the ID of the service class to which the message instance belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-serviceinstanceid-property-wmi.md">ServiceInstanceID</a></td>
<td>Contains the ID of the service instance to which the message instance belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-serviceinstancestatus-property-wmi.md">ServiceInstanceStatus</a></td>
<td>Contains state of the service instance to which this message belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-servicename-property-wmi.md">ServiceName</a></td>
<td>Contains the name of the service that corresponds to the message instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstance-servicetypeid-property-wmi.md">ServiceTypeID</a></td>
<td>Contains the ID of the service type to which the message instance belongs.</td>
</tr>
<tr class="even">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_MessageInstance** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-messageinstance-savetofile-method-wmi.md">SaveToFile</a></td>
<td>Enables an administrator to save message context and parts into multiple output files.</td>
</tr>
</tbody>
</table>


## Example

The following example displays how to limit the results of WMI queries on the MSBTS\_ServiceInstance and MSBTS\_MessageInstance WMI classes. These two WMI classes have support for WMI context properties that allow limiting a result set. This is required because the number of service instances or message instances may be very large. This is not the case for any other BizTalk WMI class and WMI context should be not used with them.

``` vb
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

No C\# sample is provided.

## Remarks

This class may have many instances, and enumerating all of these classes may be slow and unnecessarily consume resources from the MessageBox database. If the ID of the message instance is known, use it to specify the message instance in any database lookups. For example, `select * from MSBTS_MessageInstance where MessageInstanceID= "GUID"`. WMI will parse the WQL to retrieve the message ID from the query and only retrieve instances that match the specified IDs.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.