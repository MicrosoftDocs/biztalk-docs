---
title: Resuming Suspended Service Instances That Failed to be Sent to a Specific URL Using WMI
TOCTitle: Resuming Suspended Service Instances That Failed to be Sent to a Specific URL Using WMI
ms:assetid: 0f6f6dc6-43c8-4e2d-80d7-0ada8e3a2301
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547538(v=BTS.80)
ms:contentKeyID: 51526250
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Resuming Suspended Service Instances That Failed to be Sent to a Specific URL Using WMI

 

Use the following code to resume suspended service instances that failed to be sent to a specific URL.

``` csharp
using System.Management;  
  
   // This sample takes an outbound URL, queries for any suspended (resumable) service instances associating with this  
   // URL (via Send Port primary or secondary transport address) and then resume the service instances found.  The strOutboundURL  
   // supports WQL LIKE-style pattern matching.  
   //  
   // NOTE: If strOutboundURL contains any backslash characters, they must be properly escaped. (e.g. "C:\\TEMP\\Out")  
   //  
   public void ResumeSvcInstByOutboundURL(string strOutboundURL)  
   {  
      try  
      {  
         const uint SERVICE_STATUS_SUSPENDED_RESUMABLE = 4;  
         const uint REGULAR_RESUME_MODE = 1;  
  
         // Find all SendPort(s) which transmit to strOutboundURL either as primary or secondary transport address.  Comparison  
         // is done using the LIKE operator so SQL-style pattern matching can be used. (e.g. "%ABC%" will match any strings that  
         // contains "ABC" in it.  
         string strSendPortWQL = string.Format(  
            "SELECT * FROM MSBTS_SendPort WHERE PTAddress LIKE \"{0}\" OR STAddress LIKE \"{1}\"",  
            strOutboundURL, strOutboundURL);  
  
         ManagementObjectSearcher searcherSendPort = new ManagementObjectSearcher (new ManagementScope ("root\\MicrosoftBizTalkServer"), new WqlObjectQuery(strSendPortWQL), null);  
         int nNumSendPortFound = searcherSendPort.Get().Count;  
  
         if ( nNumSendPortFound > 0 )  
         {  
            bool fSvcInstFound = false;  
  
            // For each associating send port that we found  
            foreach ( ManagementObject objSendPort in searcherSendPort.Get() )  
            {  
               // Construct the WQL to find suspended service instance associating with the send port  
               string strSvcInstWQL = string.Format(  
                  "SELECT * FROM MSBTS_ServiceInstance WHERE ServiceStatus = {0} AND ServiceName = \"{1}\"",  
                  SERVICE_STATUS_SUSPENDED_RESUMABLE.ToString(), objSendPort["Name"]);  
  
               ManagementObjectSearcher searcherServiceInstance = new ManagementObjectSearcher (new ManagementScope ("root\\MicrosoftBizTalkServer"), new WqlObjectQuery(strSvcInstWQL), null);  
               int nNumSvcInstFound = searcherServiceInstance.Get().Count;  
  
               // If we found any matching suspended service instance(s)  
               if ( nNumSvcInstFound > 0 )  
               {  
                  fSvcInstFound = true;  
  
                  // Construct ID arrays to be passed into ResumeServiceInstancesByID() method  
                  string[] InstIdList = new string[nNumSvcInstFound];  
                  string[] ClassIdList = new string[nNumSvcInstFound];  
                  string[] TypeIdList = new string[nNumSvcInstFound];  
  
                  string strHost = string.Empty;  
                  string strReport = string.Empty;  
                  int i = 0;  
                  foreach ( ManagementObject objServiceInstance in searcherServiceInstance.Get() )  
                  {  
                     // It is safe to assume that all service instances of a send port belong to a single Host.  
                     if ( strHost == string.Empty )  
                        strHost = objServiceInstance["HostName"].ToString();  
  
                     ClassIdList[i] = objServiceInstance["ServiceClassId"].ToString();  
                     TypeIdList[i]  = objServiceInstance["ServiceTypeId"].ToString();  
                     InstIdList[i]  = objServiceInstance["InstanceID"].ToString();  
  
                     strReport += string.Format("  {0}\n", objServiceInstance["InstanceID"].ToString());  
                     i++;  
                  }  
  
                  // Load the MSBTS_HostQueue with Host name and invoke the "ResumeServiceInstancesByID" method  
                  string strHostQueueFullPath = string.Format("root\\MicrosoftBizTalkServer:MSBTS_HostQueue.HostName=\"{0}\"", strHost);  
                  ManagementObject objHostQueue = new ManagementObject(strHostQueueFullPath);  
  
                  // Note: The ResumeServiceInstanceByID() method processes at most 2047 service instances with each call.  
                  //   If you are dealing with larger number of service instances, this script needs to be modified to break down the  
                  //   service instances into multiple batches.  
                  objHostQueue.InvokeMethod("ResumeServiceInstancesByID",  
                     new object[] {ClassIdList, TypeIdList, InstIdList, REGULAR_RESUME_MODE}  
                     );  
  
                  Console.WriteLine( string.Format("Service instances with the following service instance IDs have been resumed:\n{0}", strReport) );  
               }  
            }  
            if ( !fSvcInstFound )  
            {  
               System.Console.WriteLine(string.Format("There is no suspended (resumable) service instance associating with outbound URL '{0}'.", strOutboundURL));  
            }  
         }  
         else  
         {  
            System.Console.WriteLine(string.Format("There is no send port associating with outbound URL '{0}'.", strOutboundURL));  
         }  
      }  
      catch(Exception excep)  
      {  
         Console.WriteLine("Error: " + excep.Message);  
      }  
   }  
```

``` 
' wbemChangeFlagEnum Setting  
const REGULAR_RESUME_MODE = 1  
  
'Module to Resume service instances  
Sub ResumeSvcInstByOutboundURL(strOutboundURL)  
  
   Dim objLocator : Set objLocator = CreateObject("WbemScripting.SWbemLocator")  
   Dim objWMIServer : Set objWMIServer = objLocator.ConnectServer(, "root/MicrosoftBizTalkServer")  
   Dim strQueryString  
   Dim objQueue  
   Dim svcInsts  
   Dim count  
   Dim inst  
  
   '=============================  
   ' Resume service instances  
   '=============================  
   On Error Resume Next  
  
   ' Find all SendPort(s) which transmit to strOutboundURL either as primary or secondary transport address.  Comparison is done  
   ' using the LIKE operator so SQL-style pattern matching can be used. (e.g. "%ABC%" will match any strings that contains "ABC" in it)  
   strQueryString = "Select * from MSBTS_SendPort where PTAddress LIKE """ & strOutboundURL & """ OR STAddress LIKE """ & strOutboundURL & """"  
   set sendPorts = objWMIServer.ExecQuery(strQueryString)  
   CheckWMIError  
  
   count = sendPorts.count  
  
   If ( count > 0 ) Then  
  
      Dim strServiceNameClause : strServiceNameClause = ""  
      Dim fSvcInstFound : fSvcInstFound = 0  
  
      ' For each associating send port that we found  
      For each sendPortInst in sendPorts  
  
         ' Construct the WQL to find suspended service instance associating with the send port  
         strQueryString = "Select * from MSBTS_ServiceInstance where ServiceStatus = 4 AND ServiceName = """ & sendPortInst.Properties_("Name") & """"  
         set svcInsts = objWMIServer.ExecQuery(strQueryString )  
         CheckWMIError  
  
         count = svcInsts.count  
  
         ' If we found any matching suspended service instance(s)  
         If ( count > 0 ) Then  
  
            fSvcInstFound = 1  
  
            Dim strHostName  
            Dim aryClassIDs()  
            Dim aryTypeIDs()  
            Dim aryInstanceIDs()  
            redim aryClassIDs(count-1)  
            redim aryTypeIDs(count-1)  
            redim aryInstanceIDs(count-1)  
  
            ' Enumerate the ServiceInstance classes to construct ID arrays to be passed into ResumeServiceInstancesByID() method  
            Dim i : i= 0  
            For each svcInst in svcInsts  
               strHostName = svcInst.Properties_("HostName")  
               aryClassIDs(i) = svcInst.Properties_("ServiceClassId")  
               aryTypeIDs(i) = svcInst.Properties_("ServiceTypeId")  
               aryInstanceIDs(i) = svcInst.Properties_("InstanceId")  
               i = i + 1  
            Next  
  
            wscript.Echo "Total suspended (resumable) service instances found for send port '" & sendPortInst.Properties_("Name") & "': " & i  
            wscript.Echo " "  
  
            'Get the HostQueue instance  
            strQueryString = "MSBTS_HostQueue.HostName=""" & strHostName & """"  
            set objQueue = objWMIServer.Get(strQueryString)  
            CheckWMIError  
  
            'Execute the Resume method of the HostQueue instance  
  
            ' Note: The ResumeServiceInstanceByID() method processes at most 2047 service instances with each call.  
            '   If you are dealing with larger number of service instances, this script needs to be modified to break down the  
            '   service instances into multiple batches.  
            objQueue.ResumeServiceInstancesByID aryClassIDs, aryTypeIDs, aryInstanceIDs, REGULAR_RESUME_MODE  
            CheckWMIError  
  
            wscript.Echo "All instances have been resumed."  
            wscript.Echo " "  
         End If  
      Next  
  
      If ( fSvcInstFound = 0 ) Then  
         wscript.echo "There is no suspended (resumable) service instance associating with outbound URL '" & strOutboundURL & "'"  
      End If'  
   Else  
      wscript.echo "There is no send port associating with outbound URL '" & strOutboundURL & "'"  
   End If  
  
   Set objLocator = Nothing  
   Set objWMIServer = Nothing  
   Set objQueue = Nothing  
   On Error Goto 0  
  
End Sub  
  
'This subroutine deals with all errors using the WbemScripting object.  Error descriptions  
'are returned to the user by printing to the console.  
Sub   CheckWMIError()  
  
   If Err <> 0   Then  
      On Error Resume   Next  
  
      Dim strErrDesc: strErrDesc = Err.Description  
      Dim ErrNum: ErrNum = Err.Number  
      Dim WMIError : Set WMIError = CreateObject("WbemScripting.SwbemLastError")  
  
      If ( TypeName(WMIError) = "Empty" ) Then  
         wscript.echo strErrDesc & " (HRESULT: "   & Hex(ErrNum) & ")."  
      Else  
         wscript.echo WMIError.Description & "(HRESULT: " & Hex(ErrNum) & ")."  
         Set WMIError = nothing  
      End   If  
  
      wscript.quit 0  
   End If  
  
End Sub  
```

## See Also

[WMI Script Samples](wmi-script-samples.md)  
[MSBTS\_SendPort (WMI)](msbts-sendport-wmi.md)  
[MSBTS\_ServiceInstance (WMI)](msbts-serviceinstance-wmi.md)  
[MSBTS\_HostQueue (WMI)](msbts-hostqueue-wmi.md)

