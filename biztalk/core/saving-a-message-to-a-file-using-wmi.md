---
title: "Saving a Message to a File Using WMI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4972da32-94f0-4478-ad24-fc2f552a447a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Saving a Message to a File Using WMI
Use the following code to save a message to a file using [MSBTS_TrackedMessageInstance](../core/msbts-trackedmessageinstance-wmi.md).  
  
```csharp  
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
  
```vbs  
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
 [WMI Script Samples](../core/wmi-script-samples.md)   
 [MSBTS_TrackedMessageInstance (WMI)](../core/msbts-trackedmessageinstance-wmi.md)