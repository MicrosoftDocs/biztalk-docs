---
title: "Creating, Updating, and Deleting a Host Instance Using WMI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620433d5-936f-476a-9480-55568c20e23f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating, Updating, and Deleting a Host Instance Using WMI
Use the following code to create, update, or delete a host instance using the [MSBTS_HostSetting](../core/msbts-hostsetting-wmi.md) class.  
  
```csharp  
using System.Management;  
  
      //Basic WMI opertaion - Create  
      //Sample to show MSBTS_HostSetting instance creation  
      public void CreateHost(string HostName, int HostType, string NTGroupName, bool AuthTrusted)  
      {  
         try  
         {  
            PutOptions options = new PutOptions();   
            options.Type = PutType.CreateOnly;  
  
            //create a ManagementClass object and spawn a ManagementObject instance  
            ManagementClass objHostSettingClass = new ManagementClass("root\\MicrosoftBizTalkServer", "MSBTS_HostSetting", null);  
            ManagementObject objHostSetting  = objHostSettingClass.CreateInstance();  
  
            //set the properties for the Managementobject  
            objHostSetting["Name"] = HostName;  
            objHostSetting["HostType"] = HostType;  
            objHostSetting["NTGroupName"] = NTGroupName;  
            objHostSetting["AuthTrusted"] = AuthTrusted;  
  
            //create the Managementobject  
            objHostSetting.Put(options);  
            System.Console.WriteLine("Host - " + HostName + " - has been created successfully");  
         }  
         catch(Exception excep)  
         {  
            System.Console.WriteLine("CreateHost - " + HostName + " - failed: " + excep.Message);  
         }  
      }  
  
      //Basic WMI opertation - Update  
      //Sample to show MSBTS_HostSetting instance update  
      public void UpdateHost(string HostName, string NTGroupName, bool AuthTrusted)  
      {  
         try  
         {  
            PutOptions options = new PutOptions();  
            options.Type = PutType.UpdateOnly;  
  
            ManagementObject objHostSetting = new ManagementObject();  
            objHostSetting.Scope = new ManagementScope("root\\MicrosoftBizTalkServer");  
  
            //define lookup query  
            string strQuery = "MSBTS_HostSetting.Name='" + HostName + "'";  
            objHostSetting.Path = new ManagementPath(strQuery);  
  
            //redefine properties value  
            objHostSetting["NTGroupName"] = NTGroupName;  
            objHostSetting["AuthTrusted"] = AuthTrusted;  
  
            //update the ManagementObject  
            objHostSetting.Put(options);  
            System.Console.WriteLine("Host - " + HostName + " - has been updated successfully");  
         }  
         catch(Exception excep)  
         {  
            System.Console.WriteLine("UpdateHost - " + HostName + " - failed: " + excep.Message);  
         }  
      }  
  
      //Basic WMI opertaion - Delete  
      //Sample to show MSBTS_HostSetting instance Delete  
      public void DeleteHost(string HostName)  
      {  
         try  
         {  
            ManagementObject objHostSetting = new ManagementObject();  
            objHostSetting.Scope = new ManagementScope("root\\MicrosoftBizTalkServer");  
  
            //define lookup query  
            string strQuery = "MSBTS_HostSetting.Name='" + HostName + "'";  
            objHostSetting.Path = new ManagementPath(strQuery);  
  
            //delete the Managementobject  
            objHostSetting.Delete();  
  
            System.Console.WriteLine("Host - " + HostName + " - has been deleted successfully");  
         }  
         catch(Exception excep)  
         {  
            System.Console.WriteLine("DeleteHost - " + HostName + " - failed: " + excep.Message);  
         }  
      }  
```  
  
```vbs  
Option Explicit  
  
' wbemChangeFlagEnum Setting  
const UpdateOnly = 1  
const CreateOnly = 2  
  
' Basic WMI operation - Create  
' Sample to show MSBTS_HostSetting instance creation  
Sub CreateHost (HostName, HostType, NTGroupName, AuthTrusted)  
   On Error Resume Next  
  
   Dim objLocator, objService, objHostSetting, objHS  
  
   ' Connects to local server WMI Provider BizTalk namespace  
   Set objLocator = Createobject ("wbemScripting.SWbemLocator")  
   Set objService = objLocator.ConnectServer(".", "root/MicrosoftBizTalkServer")  
  
   ' Get WMI class MSBTS_HostSetting  
   Set objHostSetting = objService.Get ("MSBTS_HostSetting")  
  
   Set objHS = objHostSetting.SpawnInstance_  
  
   objHS.Name = HostName  
   objHS.HostType = HostType  
   objHS.NTGroupName = NTGroupName  
   objHS.AuthTrusted = AuthTrusted  
  
   ' Create instance  
   objHS.Put_(CreateOnly)  
  
   CheckWMIError  
   wscript.echo "Host - " & HostName & " - has been created successfully"  
  
end Sub  
  
' Basic WMI operation - Update  
' Sample to show MSBTS_HostSetting instance update  
Sub UpdateHost (HostName, NTGroupName, AuthTrusted)  
   On Error Resume Next  
  
   Dim objLocator, objService, objHS  
  
   ' Connects to local server WMI Provider BizTalk namespace  
   Set objLocator = Createobject ("wbemScripting.SWbemLocator")  
   Set objService = objLocator.ConnectServer(".", "root/MicrosoftBizTalkServer")  
  
   ' Look for WMI Class MSBTS_HostSetting with name equals HostName value  
   Set objHS = objService.Get("MSBTS_HostSetting.Name='" & HostName & "'")  
  
   objHS.NTGroupName = NTGroupName  
   objHS.AuthTrusted = AuthTrusted  
  
   ' Update instance properties  
   objHS.Put_(UpdateOnly)  
  
   ' Check for error condition before continuing.  
   CheckWMIError  
   wscript.echo "Host - " & HostName & " - has been updated successfully"  
  
end Sub  
  
' Basic WMI operation - Delete  
' Sample to show MSBTS_HostSetting instance deletion  
Sub DeleteHost (HostName)  
   On Error Resume Next  
  
   Dim objLocator, objService, objHS  
  
   ' Connects to local server WMI Provider BizTalk namespace  
   Set objLocator = Createobject ("wbemScripting.SWbemLocator")  
   Set objService = objLocator.ConnectServer(".", "root/MicrosoftBizTalkServer")  
  
   ' Look for WMI Class MSBTS_HostSetting with name equals HostName value  
   Set objHS = objService.Get("MSBTS_HostSetting.Name='" & HostName & "'")  
  
   ' Delete instance  
   objHS.Delete_  
  
   ' Check for error condition before continuing.  
   CheckWMIError  
   wscript.echo "Host - " & HostName & " - has been deleted successfully"  
  
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
 [MSBTS_HostSetting (WMI)](../core/msbts-hostsetting-wmi.md)