---
description: "Learn more about: Removing Suspended Service Instances"
title: Removing Suspended Service Instances
TOCTitle: Removing Suspended Service Instances
ms:assetid: 92a4378f-96fd-44b2-afe6-d3de6e129493
ms:mtpsurl: https://msdn.microsoft.com/library/Bb203857(v=BTS.80)
ms:contentKeyID: 51529732
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: concept-article
---

# Removing Suspended Service Instances

 

Use the following code to delete suspended service instances.

```C#
' terminate.vbs  
' Enter terminate.vbs with no arguments from a command prompt for usage  
' This script needs to be run under a user account that is a member of the BizTalk Administrators   
' group. This script needs to be run on a machine that is configured with BizTalk administration  
' tools.  
  
dim objBtsWmiNS, objMsg, svcinsts, inst, msg, ndx, size, savemessages  
  
Dim aryClassIDs()  
Dim aryTypeIDs()  
Dim aryInstanceIDs()  
Dim aryHostNames()  
Dim aryObjQueues()  
Dim aryHostBatchSize()  
  
Dim strKey2Instance  
Dim strQuery2Msg  
maxBatchSize = 200 'Terminate in batches. Max supported batch size is 2K-1 (2047)  
  
On Error Resume Next  
Dim objArgs: Set objArgs = WScript.Arguments  
If ( objArgs.Count = 0 OR objArgs.Count > 2) Then  
     PrintUsage()  
     wscript.quit 0  
End If  
  
wmiQuery = ""  
  
'ServiceStatus = 16 - 'Completed With Discarded Messages' in BizTalk Server 2004  
'ServiceStatus = 32 - 'Suspended (not resumable)'  
'ServiceStatus = 4 - 'Suspended (resumable)'  
'ServiceClass = 64 - 'Routing Failure Report'  
'ErrorId = "0xC0C01B4C" - is how 'Completed With Discarded Messages' are exposed in BizTalk Server 2009  
  
If (objArgs(0) = "-Z" OR objArgs(0) = "-z") Then  
     wmiQuery = "select * from MSBTS_serviceinstance where ServiceStatus=16"  
End If  
  
If (objArgs(0) = "-A" or objArgs(0) = "-a") Then  
     wmiQuery = "select * from MSBTS_serviceinstance where ServiceStatus=4 OR ServiceStatus=32 OR ServiceStatus=16 OR ErrorId='0xC0C01B4C' OR ServiceClass=64"  
End If  
  
If (objArgs(0) = "-SR" or objArgs(0) = "-sr") Then  
     wmiQuery = "select * from MSBTS_serviceinstance where ServiceStatus=4"  
End If  
  
If (objArgs(0) = "-SNR" or objArgs(0) = "-snr") Then  
     wmiQuery = "select * from MSBTS_serviceinstance where ServiceStatus=32"  
End If  
  
If (objArgs(0) = "-DIS" or objArgs(0) = "-dis") Then  
     wmiQuery = "select * from MSBTS_serviceinstance where ServiceClass=32 AND ServiceStatus=8"  
'ServiceClass = 32 'Isolated Adapter  
'ServiceStatus = 8 'Dehydrated  
End If  
  
saveMessagesBeforeTermination = True  
If ( objArgs.Count > 1) Then  
     If (objArgs(1) = "-NOSAVE" OR objArgs(1) = "-nosave") Then  
          saveMessagesBeforeTermination = False  
     Else  
          PrintUsage()  
          wscript.quit 0  
     End If  
End If  
  
If(wmiQuery = "") Then  
     PrintUsage()  
     wscript.quit 0  
End If  
  
wscript.echo "-->Connecting to BizTalk WMI namespace"  
Set objBtsWmiNS = GetObject("WinMgmts:{impersonationLevel=impersonate, (security)}\\.\root\MicrosoftBizTalkServer")   
If Err <> 0 Then  
     CheckWMIError  
     wscript.quit 0  
End If          
  
wscript.echo "-->Getting BizTalk host collection"  
Set hosts = objBtsWmiNS.ExecQuery("select * from MSBTS_HostSetting")  
If Err <> 0 Then  
     CheckWMIError  
     wscript.quit 0  
End If          
  
hostCount = hosts.count  
  
ReDim aryHostNames(hostCount - 1)  
ReDim aryObjQueues(hostCount - 1)  
ReDim aryHostBatchSize(hostCount - 1)  
  
wscript.echo "-->Retrieve BizTalk host names and loading host queues"  
ndx = 0  
For Each host in hosts  
     wscript.echo "Found host " & host.Properties_("Name")  
     aryHostNames(ndx) = host.Properties_("Name")  
     Set aryObjQueues(ndx) = objBtsWmiNS.Get("MSBTS_HostQueue.HostName=""" & aryHostNames(ndx) & """")  
     If Err <> 0 Then  
          CheckWMIError  
          wscript.quit 0  
     End If          
     ndx = ndx + 1  
Next  
  
wscript.echo "-->Getting collection of service instances"  
Set svcinsts = objBtsWmiNS.ExecQuery(wmiQuery)  
  
ReDim aryClassIDs(hostCount, maxBatchSize-1)  
ReDim aryTypeIDs(hostCount, maxBatchSize-1)  
ReDim aryInstanceIDs(hostCount, maxBatchSize-1)  
  
'Iterate through instances and save them in host-specific arrays.  
'Terminate instances from host-specific array when array gets to a maxBatchSize  
wscript.echo "-->Start iterating service instances"  
totalCount = 0  
saveMessages = saveMessagesBeforeTermination  
For Each inst in svcinsts  
     saveMessagesBeforeTermination = saveMessages  
     wscript.echo "Found suspended instance """ & inst.Properties_("ServiceName") & """ on host " & inst.Properties_("HostName")  
     'Resolve host index  
     For hostIdx = 0 To hostCount-1   
          If aryHostNames(hostIdx) = inst.Properties_("HostName") Then  
               Exit For  
          End If  
     Next  
  
    '16 is an internal service class that cannot be terminated  
     If 16 = inst.Properties_("ServiceClass") Then  
          wscript.echo "Skipping BizTalk internal service instances (they cannot be terminated anyway)"  
     Else  
          '64 is a routing failure report and doesn't have messages that can be saved  
          If 64 = inst.Properties_("ServiceClass") Or 16 = inst.Properties_("ServiceClass") Then  
               saveMessagesBeforeTermination = False  
          End If  
  
          errorCountSavingMessages = 0  
          If saveMessagesBeforeTermination Then  
               strQuery2Msg = "select * from MSBTS_MessageInstance where ServiceInstanceID=""" & inst.Properties_("InstanceId") & """"  
               Set msgInsts = objBtsWmiNS.ExecQuery(strQuery2Msg)  
               For Each msg in msgInsts  
                    msg.SaveToFile "C:\Temp"  
                  If Err <> 0 Then  
                         CheckWMIError  
                       wscript.echo "Failed to save MSBTS_MessageInstance"  
                       wscript.echo Err.Description & Err.Number  
                       errorCountSavingMessages = errorCountSavingMessages + 1  
                  Else  
                         wscript.echo "Saved message " & msg.Properties_("MessageInstanceID")  
                  End If          
              Next  
         End If  
  
         If 0 = errorCountSavingMessages Then 'Only terminate when we had no problems saving messages  
               aryClassIDs(hostIdx, aryHostBatchSize(hostIdx)) = inst.Properties_("ServiceClassId")  
               aryTypeIDs(hostIdx, aryHostBatchSize(hostIdx)) = inst.Properties_("ServiceTypeId")  
               aryInstanceIDs(hostIdx, aryHostBatchSize(hostIdx)) = inst.Properties_("InstanceId")  
               aryHostBatchSize(hostIdx) = aryHostBatchSize(hostIdx) + 1 'Keep track of newly added instace for that host  
          Else  
               wscript.echo "Skipping the instance since couldn't save its messages"  
          End If  
  
          totalCount = totalCount + 1  
          If(aryHostBatchSize(hostIdx) = maxBatchSize) Then  
               TerminateAccumulatedInstacesForHost hostIdx  
          End If  
     End If  
Next  
  
' Delete whatever is left  
For hostIdx = 0 To hostCount-1   
     If aryHostBatchSize(hostIdx) > 0 Then  
          TerminateAccumulatedInstacesForHost hostIdx  
     End If  
Next  
  
wscript.echo "SUCCESS> " & totalCount & " instances were found and attempted to be terminated"  
  
Sub     TerminateAccumulatedInstacesForHost(hostIdx)  
     wscript.echo "Sending termination request for host " & aryHostNames(hostIdx) & " service instances"  
     Dim aryClassIDs4Host()  
     Dim aryTypeIDs4Host()  
     Dim aryInstanceIDs4Host()  
     ReDim aryClassIDs4Host(aryHostBatchSize(hostIdx)-1)  
     ReDim aryTypeIDs4Host(aryHostBatchSize(hostIdx)-1)  
     ReDim aryInstanceIDs4Host(aryHostBatchSize(hostIdx)-1)  
  
     For i = 0 to aryHostBatchSize(hostIdx)-1  
          aryClassIDs4Host(i) = aryClassIDs(hostIdx, i)  
          aryTypeIDs4Host(i) = aryTypeIDs(hostIdx, i)  
          aryInstanceIDs4Host(i) = aryInstanceIDs(hostIdx, i)  
     Next  
     aryObjQueues(hostIdx).TerminateServiceInstancesByID aryClassIDs4Host, aryTypeIDs4Host, aryInstanceIDs4Host  
     CheckWMIError  
     aryHostBatchSize(hostIdx) = 0  
End Sub  
  
'This subroutine deals with all errors using the WbemScripting object.    
'Error descriptions are returned to the user by printing to the console.  
Sub CheckWMIError()  
  
     If Err <> 0 Then  
          On Error Resume Next  
          Dim strErrDesc: strErrDesc = Err.Description  
          Dim ErrNum: ErrNum = Err.Number  
          Dim WMIError : Set WMIError = CreateObject("WbemScripting.SwbemLastError")  
  
          If (TypeName(WMIError) = "Empty" ) Then  
               wscript.echo strErrDesc & " (HRESULT: " & Hex(ErrNum) & ")."  
          Else  
               wscript.echo WMIError.Description & "(HRESULT: " & Hex(ErrNum) & ")."  
               Set WMIError = nothing  
          End If  
  
          'wscript.quit 0  
     End If  
  
End Sub   
  
Sub PrintUsage()  
     wscript.echo "Usage:"  
     wscript.echo "cscript Terminate.vbs < -Z | -A | -DIS | -SR | -SNR > [-nosave]"  
     wscript.echo  
     wscript.echo "  -Z terminates all ""Zombie"" instances (e.g. completed with discarded messages)"  
     wscript.echo "  -A terminates all suspended and zombie instances as well as all routing failure reports"  
     wscript.echo "  -SR terminates suspended resumable instances only"  
     wscript.echo "  -SNR terminates suspended non-resumable instances only"  
     wscript.echo "  -DIS terminates all dehydrated 'isolated adapter' instances"  
     wscript.echo "  -nosave terminates instances without saving messages they reference"  
     wscript.echo "  Default action is to save instances to the C:\Temp folder on the local computer"  
     wscript.echo  
     wscript.echo "  Ensure that the C:\Temp folder exists before running terminate if you want to save instances"  
     wscript.echo  
     wscript.echo "  Example: cscript Terminate.vbs -z -nosave"  
     wscript.echo  
End Sub  
```

