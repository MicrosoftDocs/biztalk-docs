---
title: Resuming Suspended Service Instances of a Specific Orchestration Using WMI
TOCTitle: Resuming Suspended Service Instances of a Specific Orchestration Using WMI
ms:assetid: 87d93c70-0443-4b4d-a44b-896a5b2556cb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561219(v=BTS.80)
ms:contentKeyID: 51529470
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Resuming Suspended Service Instances of a Specific Orchestration Using WMI

 

Use the following code to resume suspended service instances of a specific orchestration using the [MSBTS\_HostQueue](msbts-hostqueue-wmi.md) class.

``` csharp
using System.Management;  
  
        public void ResumeSvcInstByOrchestrationName(string strOrchestrationName)  
        {  
            try  
            {  
                const uint SERVICE_CLASS_ORCHESTRATION = 1;  
                const uint SERVICE_STATUS_SUSPENDED_RESUMABLE = 4;  
                const uint REGULAR_RESUME_MODE = 1;  
  
                // Query for suspended (resumable) service instances of the specified orchestration  
                // Suggestion: Similar queries can be written for Suspend/Terminate operations by using different ServiceStatus value.  See MOF definition for details.  
                string strWQL = string.Format(  
                    "SELECT * FROM MSBTS_ServiceInstance WHERE ServiceClass = {0} AND ServiceStatus = {1} AND ServiceName = \"{2}\"",  
                    SERVICE_CLASS_ORCHESTRATION.ToString(), SERVICE_STATUS_SUSPENDED_RESUMABLE.ToString(), strOrchestrationName);  
  
                ManagementObjectSearcher searcherServiceInstance = new ManagementObjectSearcher (new ManagementScope ("root\\MicrosoftBizTalkServer"), new WqlObjectQuery(strWQL), null);  
                int nNumSvcInstFound = searcherServiceInstance.Get().Count;  
  
                // If we found any  
                if ( nNumSvcInstFound > 0 )  
                {  
                    // Construct ID arrays to be passed into ResumeServiceInstancesByID() method  
                    string[] InstIdList = new string[nNumSvcInstFound];  
                    string[] ClassIdList = new string[nNumSvcInstFound];  
                    string[] TypeIdList = new string[nNumSvcInstFound];  
  
                    string strHost = string.Empty;  
                    string strReport = string.Empty;  
                    int i = 0;  
                    foreach ( ManagementObject objServiceInstance in searcherServiceInstance.Get() )  
                    {  
                        // It is safe to assume that all service instances belong to a single Host.  
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
                else  
                {  
                    System.Console.WriteLine(string.Format("There is no suspended (resumable) service instance found for orchestration '{0}'.", strOrchestrationName));  
                }  
            }  
            catch(Exception excep)  
            {  
                Console.WriteLine("Error: " + excep.Message);  
            }  
        }  
[VBScript]   
' wbemChangeFlagEnum Setting  
const REGULAR_RESUME_MODE = 1  
  
'Module to Resume service instances  
Sub ResumeServiceInstance(strOrchestrationName)  
  
   Dim objLocator : Set objLocator = CreateObject("WbemScripting.SWbemLocator")  
   Dim objServices : Set objServices = objLocator.ConnectServer(, "root/MicrosoftBizTalkServer")  
   Dim strQueryString  
   Dim objQueue  
   Dim svcInsts  
   Dim count  
   Dim inst  
  
   '=============================  
   ' Resume service instances  
   '=============================  
   wscript.Echo "Bulk Resuming service instances - "  
   Wscript.Echo ""  
  
   On Error Resume Next  
  
   ' Query for suspended (resumable) service instances of the specified orchestration  
   ' Suggestion: Similar queries can be written for Suspend/Terminate operations by using different ServiceStatus value.  See MOF definition for details.  
   set svcInsts = objServices.ExecQuery("Select * from MSBTS_ServiceInstance where ServiceClass = 1 AND ServiceStatus = 4 AND ServiceName = """ & strOrchestrationName & """")  
   count = svcInsts.count  
  
   If ( count > 0 ) Then  
  
      Dim strHostName  
      Dim aryClassIDs()  
      Dim aryTypeIDs()  
      Dim aryInstanceIDs()  
      redim aryClassIDs(count-1)  
      redim aryTypeIDs(count-1)  
      redim aryInstanceIDs(count-1)  
  
      ' Enumerate the ServiceInstance classes to construct ID arrays to be passed into ResumeServiceInstancesByID() method  
      Dim i : i= 0  
      For each inst in svcInsts  
         strHostName = inst.Properties_("HostName")  
         aryClassIDs(i) = inst.Properties_("ServiceClassId")  
         aryTypeIDs(i) = inst.Properties_("ServiceTypeId")  
         aryInstanceIDs(i) = inst.Properties_("InstanceId")  
         i = i + 1  
      Next  
  
      wscript.Echo "Total instances found during enumeration: " & i  
      wscript.Echo " "  
  
      'Get the HostQueue instance  
      strQueryString = "MSBTS_HostQueue.HostName=""" & strHostName & """"  
      set objQueue = objServices.Get(strQueryString)  
      CheckWMIError  
  
      'Execute the Resume method of the HostQueue instance  
  
      ' Note: The ResumeServiceInstanceByID() method processes at most 2047 service instances with each call.  
      '   If you are dealing with larger number of service instances, this script needs to be modified to break down the  
      '   service instances into multiple batches.  
      objQueue.ResumeServiceInstancesByID aryClassIDs, aryTypeIDs, aryInstanceIDs, REGULAR_RESUME_MODE  
      CheckWMIError  
  
      Wscript.Echo ""  
      wscript.Echo "Instances resumed - " &  i & ""  
  
   Else  
      wscript.echo "There is no suspended (resumable) service instance found for orchestration '" & strOrchestrationName & "'"  
   End If  
  
   Set objLocator = Nothing  
   Set objServices = Nothing  
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
[MSBTS\_HostQueue (WMI)](msbts-hostqueue-wmi.md)

