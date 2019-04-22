---
title: Saving a Message to a File Using WMI
TOCTitle: Saving a Message to a File Using WMI
ms:assetid: 4972da32-94f0-4478-ad24-fc2f552a447a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559958(v=BTS.80)
ms:contentKeyID: 51527810
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Saving a Message to a File Using WMI

 

Use the following code to save a message to a file using [MSBTS\_TrackedMessageInstance](msbts-trackedmessageinstance-wmi.md).

``` csharp
using System.Management;  
  
      //Sample to show how to save a tracked message out to a file folder using MSBTS_TrackedMessageInstance class  
      public void SaveTrackedMessageInstanceToFolder(Guid MessageInstanceId, string strOutputFolder)  
      {  
         try  
         {  
            // Construct full WMI path to the MSBTS_TrackedMessageInstance using the message guid (NOTE: MessageInstanceID string value must be enclosed in {} curly brackets)  
            string strInstanceFullPath = "root\\MicrosoftBizTalkServer:MSBTS_TrackedMessageInstance.MessageInstanceID='{" + MessageInstanceId.ToString() + "}'";  
  
            // Load the MSBTS_TrackedMessageInstance  
            ManagementObject objTrackedSvcInst = new ManagementObject(strInstanceFullPath);  
  
            // Invoke "SaveToFile" method to save the message out into the specified folder  
            objTrackedSvcInst.InvokeMethod("SaveToFile", new object[] {strOutputFolder});  
         }  
         catch(Exception excep)  
         {  
            Console.WriteLine("Failed to save tracked message with id " + MessageInstanceId.ToString() + " into folder " + strOutputFolder + ": " + excep.Message);  
         }  
      }     
```

``` VBScript
Option Explicit  
  
Sub SaveTrackedMessageInstanceToFolder(strMessageInstanceId, strOutputFolder)  
  
   On Error Resume Next  
  
   ' Construct full WMI path to the MSBTS_TrackedMessageInstance using the message guid (NOTE: MessageInstanceID string value must be enclosed in {} curly brackets)  
   Dim strInstanceFullPath : strInstanceFullPath = "MSBTS_TrackedMessageInstance.MessageInstanceID=""{" & strMessageInstanceId & "}"""  
  
   ' Load the MSBTS_TrackedMessageInstance  
   Dim objLocator : Set objLocator = CreateObject("WbemScripting.SWbemLocator")  
   Dim objServices : Set objServices = objLocator.ConnectServer(, "root/MicrosoftBizTalkServer")  
   CheckWMIError  
  
   Dim objTrackedMsgInst : Set objTrackedMsgInst = objServices.Get(strInstanceFullPath)  
   CheckWMIError  
  
   ' Invoke "SaveToFile" method to save the message out into the specified folder  
   objTrackedMsgInst.SaveToFile strOutputFolder  
   CheckWMIError  
  
   wscript.echo "Successfully saved tracked message with ID '" & strMessageInstanceId & "' into folder '" & strOutputFolder &"'"  
  
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
[MSBTS\_TrackedMessageInstance (WMI)](msbts-trackedmessageinstance-wmi.md)

