---
description: "Learn more about: Uninstalling and Un-Mapping a Host Instance Using WMI"
title: Uninstalling and Un-Mapping a Host Instance Using WMI
TOCTitle: Uninstalling and Un-Mapping a Host Instance Using WMI
ms:assetid: ef76bcba-7faa-4d40-b243-0d8d08120632
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561820(v=BTS.80)
ms:contentKeyID: 51533272
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Uninstalling and Un-Mapping a Host Instance Using WMI

 

Use the following code to uninstall and un-map a host instance using [MSBTS\_HostInstance](msbts-hostinstance-wmi.md) and [MSBTS\_ServerHost](msbts-serverhost-wmi.md) classes.

``` csharp
using System.Management;  
  
//Function to UnInstall and then UnMap a HostInstance using MSBTS_HostInstance and MSBTS_ServerHost  
      public void UnInstallAndUnMap(string hostName, string svrName )  
      {  
         try  
         {  
            //Build the HostInstance name  
            string hostInstanceName = "Microsoft BizTalk Server" //Name of product  
               + " " + hostName //Name of Host of which instance is to be deleted  
               + " " + svrName; //Name of Server on which instance is to be deleted  
  
            //Get the options and create a new ManagementClass  
            ObjectGetOptions hostInstOptions = new ObjectGetOptions();  
            ManagementClass hostInstClass = new ManagementClass("root\\MicrosoftBizTalkServer","MSBTS_HostInstance",hostInstOptions);  
            //Specify the enumeration options and retrieve instances of the HostInstance class  
            EnumerationOptions enumOptions = new EnumerationOptions();  
            enumOptions.ReturnImmediately = false;  
            ManagementObjectCollection hostInstCollection = hostInstClass.GetInstances(enumOptions);  
  
            ManagementObject hostInstance = null;  
  
            //Iterate through the collection and retrieve the specific HostInstance that is required  
            foreach(ManagementObject inst in hostInstCollection)  
            {  
               if(inst["Name"] != null)  
               {  
                  if (inst["Name"].ToString().ToUpper() == hostInstanceName.ToUpper())  
                  {  
                      hostInstance = inst;  
                  }  
  
               }  
  
            }  
  
            //Stop the HostInstance if it is 'Started' and if it is an InProcess HostInstance  
            if(hostInstance["HostType"].ToString() != "2" && hostInstance["ServiceState"].ToString() == "4")  
            {  
               hostInstance.InvokeMethod("Stop",null);  
            }  
  
            //Now UnInstall the HostInstance  
            hostInstance.InvokeMethod("UnInstall",null);  
  
            //Create an instance of the ServerHost class using the System.Management namespace  
            ObjectGetOptions svrHostOptions = new ObjectGetOptions();  
            ManagementClass svrHostClass = new ManagementClass("root\\MicrosoftBizTalkServer","MSBTS_ServerHost",svrHostOptions);  
            ManagementObject svrHostObject = svrHostClass.CreateInstance();  
  
            //Set the properties of the ServerHost instance  
            svrHostObject["ServerName"] = svrName;  
            svrHostObject["HostName"] = hostName;   
  
            //Invoke the UnMap method of the ServerHost object  
            svrHostObject.InvokeMethod("UnMap",null);  
  
            Console.WriteLine("HostInstance was uninstalled and unmapped successfully. Mapping deleted between Host: " + hostName + " and Server: " + svrName);  
            return;  
         }  
            catch(Exception excep)  
         {  
            Console.WriteLine("Failure during HostInstance deletion - " + excep.Message);  
         }  
      }  
```

``` VBScript
Option Explicit  
  
' Host Instance status number  
Const HostInstServiceState_Running = 4  
Const HostInstConfigState_NotInstalled = 5  
  
' Uninstall and unmap a host instance using MSBTS_ServerHost and MSBTS_HostInstance  
Sub UnMapUninstallHostInstance (HostName, ServerName)  
   On Error Resume Next  
  
   Dim Query, HostInstanceName, HostInstSet, Inst, ServerHostSet  
  
   HostInstanceName = "Microsoft BizTalk Server " & HostName & " " & ServerName  
  
   ' Step 1 - Uninstall the host instance using MSBTS_HostInstance class  
   ' Only one instance will be returned becasue Name value is unique  
   Query = "SELECT * FROM MSBTS_HostInstance WHERE Name =""" & HostInstanceName & """"  
   Set HostInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(Query)  
  
   If HostInstSet.Count > 0 Then  
      For Each Inst in HostInstSet  
  
         ' If host instance is running, then we need to first stop it  
             If( HostInstServiceState_Running = Inst.ServiceState ) Then  
            wscript.echo "Stopping host instance..."  
                Inst.Stop   ' Calling MSBTS_HostInstance::Stop() method  
            CheckWMIError  
            wscript.echo "HostInstance - " & HostName & " - has been stopped successfully on server - " & ServerName  
         End If  
  
         If ( HostInstConfigState_NotInstalled <> Inst.ConfigurationState ) Then  
  
            Inst.uninstall      ' Calling MSBTS_HostInstance::Uninstall() method  
            CheckWMIError  
            wscript.echo "HostInstance - " & HostName & " - has been uninstalled successfully from server - " & ServerName  
         End If  
      Next  
   End If  
  
   ' Step 2 - Delete mapping between server and host using MSBTS_ServerHost class  
   ' Only one instance will be returned from this query  
   Query = "SELECT * FROM MSBTS_ServerHost WHERE HostName =""" & HostName & """ AND ServerName = """ & ServerName & """"  
   Set ServerHostSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(Query)  
  
   If ServerHostSet.Count > 0 Then  
      For Each Inst In ServerHostSet  
             If( -1 = Inst.IsMapped ) Then  
  
                Inst.Unmap   ' Calling MSBTS_ServerHost::Unmap() method  
            CheckWMIError  
  
            wscript.echo "HostInstance - " & HostName & " - has been unmapped successfully from server - " & ServerName  
         Else  
            wscript.echo "HostInstance - " & HostName & " - is not unmapped from server - " & ServerName  
             End If  
      Next  
   Else  
      wscript.echo "Server """ & ServerName & """ and Host """ & HostName & """ cannot be unmapped because either the specified server or host is invalid."  
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

[WMI Script Samples](wmi-script-samples.md)  
[MSBTS\_ServerHost (WMI)](msbts-serverhost-wmi.md)  
[MSBTS\_HostInstance (WMI)](msbts-hostinstance-wmi.md)

