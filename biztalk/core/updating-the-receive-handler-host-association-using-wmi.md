---
title: "Updating the Receive Handler Host Association Using WMI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4de658e6-bbb4-4488-b80b-6ebdc0f72a21
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Updating the Receive Handler Host Association Using WMI
Use the following code to update the [MSBTS_ReceiveHandler](../core/msbts-receivehandler-wmi.md) host association.  
  
```csharp  
using System.Management;  
  
      //Sample to show MSBTS_HostSetting host association update  
      public void UpdateReceiveHandler(string AdapterName, string HostName, string HostNameToSwitchTo)  
      {  
         try  
         {  
            PutOptions options = new PutOptions();  
            options.Type = PutType.UpdateOnly;  
  
            //Look for the target WMI Class MSBTS_ReceiveHandler instance  
            string strWQL = "SELECT * FROM MSBTS_ReceiveHandler WHERE AdapterName =\"" + AdapterName + "\" AND HostName = \"" + HostName + "\"";  
            ManagementObjectSearcher searcherReceiveHandler = new ManagementObjectSearcher (new ManagementScope ("root\\MicrosoftBizTalkServer"), new WqlObjectQuery(strWQL), null);  
  
            if (searcherReceiveHandler.Get().Count > 0)  
               foreach (ManagementObject objReceiveHandler in searcherReceiveHandler.Get())  
               {  
                  //update host association  
                  objReceiveHandler["HostNameToSwitchTo"] = HostNameToSwitchTo;  
                  //update the ManagementObject  
                  objReceiveHandler.Put(options);  
                  System.Console.WriteLine("ReceiveHandler - " + AdapterName + " " + HostNameToSwitchTo + " - has been updated successfully");  
               }  
            else  
               System.Console.WriteLine("ReceiveHandler - " + AdapterName + " " + HostName + " - cannot be found");                 
         }  
         catch(Exception excep)  
         {  
            System.Console.WriteLine("UpdateReceiveHandler - " + AdapterName + " " + HostName + " - failed: " + excep.Message);  
         }  
      }  
```  
  
```vbs  
Option Explicit  
  
' wbemChangeFlagEnum Setting  
const UpdateOnly = 1  
  
' Sample to show MSBTS_ReceiveHandler host association update  
Sub UpdateReceiveHandler (AdapterName, HostName, HostNameToSwitchTo)  
   On Error Resume Next  
  
   Dim Query, ReceiveHandlerInstSet, Inst  
  
   ' Look for the target WMI Class MSBTS_ReceiveHandler instance  
   Query = "SELECT * FROM MSBTS_ReceiveHandler WHERE AdapterName =""" & AdapterName & """ AND HostName = """ & HostName & """"  
   Set ReceiveHandlerInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(Query)  
  
   If ReceiveHandlerInstSet.Count > 0 Then  
      For Each Inst In ReceiveHandlerInstSet  
         ' Update host association  
         Inst.HostNameToSwitchTo = HostNameToSwitchTo  
         Inst.Put_(UpdateOnly)  
  
         ' Check for error condition before continuing.  
         CheckWMIError  
         wscript.echo "Receive Handler - " & AdapterName & " " & HostNameToSwitchTo & " - has been updated successfully"  
      Next  
   Else  
      wscript.echo "Receive Handler - " & AdapterName & " " & HosTName & " - cannot be found"  
      wscript.quit 0  
   End If  
  
end Sub  
  
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
 [MSBTS_ReceiveHandler (WMI)](../core/msbts-receivehandler-wmi.md)