---
title: Mapping and Installing Host Instances Using WMI
TOCTitle: Mapping and Installing Host Instances Using WMI
ms:assetid: 67c82dc7-719e-4e75-ab00-a908240b43fa
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560568(v=BTS.80)
ms:contentKeyID: 51528634
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Mapping and Installing Host Instances Using WMI

 

Use the following code to map and install host instances using the [MSBTS\_ServerHost](msbts-serverhost-wmi.md) and [MSBTS\_HostInstance](msbts-hostinstance-wmi.md) classes.

``` csharp
using System.Management;  
  
//Function to Map and Install a HostInstance using MSBTS_ServerHost and MSBTS_HostInstance  
      public void MapAndInstall(string hostName, string svrName, string uid, string pwd)  
      {  
         try  
         {  
            //Build the name of the HostInstance - name has to be in the below format  
            string hostInstanceName = "Microsoft BizTalk Server" //Name of product  
                              + " " + hostName         //Name of Host of which instance is to be created  
                              + " " + svrName;         //Name of Server on which instance is to be created  
  
            //Create an instance of the ServerHost class using the System.Management namespace  
            ObjectGetOptions svrHostOptions = new ObjectGetOptions();  
            ManagementClass svrHostClass = new ManagementClass("root\\MicrosoftBizTalkServer","MSBTS_ServerHost",svrHostOptions);  
            ManagementObject svrHostObject = svrHostClass.CreateInstance();  
  
            //Set the properties of the ServerHost instance  
            svrHostObject["ServerName"] = svrName;  
            svrHostObject["HostName"] = hostName;  
  
            //Invoke the Map method of the ServerHost instance  
            svrHostObject.InvokeMethod("Map",null);  
  
            //Create an instance of the HostInstance class using the System.Management namespace  
            ObjectGetOptions hostInstOptions = new ObjectGetOptions();  
            ManagementClass hostInstClass = new ManagementClass("root\\MicrosoftBizTalkServer","MSBTS_HostInstance",hostInstOptions);  
            ManagementObject hostInstObject = hostInstClass.CreateInstance();  
  
            //Set the properties of the HostInstance class  
            hostInstObject["Name"] = hostInstanceName;  
  
            //Build a parameter array  
            object [] args = new object[2];  
            args[0] = uid;  
            args[1] = pwd;  
  
            //Invoke the Install method of the HostInstance  
            hostInstObject.InvokeMethod("Install",args);  
  
            Console.WriteLine("HostInstance was mapped and installed successfully. Mapping created between Host: " + hostName + " and Server: " + svrName);  
                         return;  
         }  
         catch(Exception excep)  
         {  
            Console.WriteLine("Failure during HostInstance creation: " + excep.Message);  
         }  
      }  
```

``` VBScript
Option Explicit  
  
' Map and install a host instance using MSBTS_ServerHost and MSBTS_HostInstance  
Sub MapInstallHostInstance (HostName, ServerName, uid, pwd)  
   On Error Resume Next  
  
   Dim objLocator, objService, objServerHost, objSH  
   Dim objHostInstance, objHI  
  
   ' Connects to local server WMI Provider BizTalk namespace  
   Set objLocator = Createobject ("wbemScripting.SWbemLocator")  
   Set objService = objLocator.ConnectServer(".", "root/MicrosoftBizTalkServer")  
  
   ' Step 1 - Create mapping between server and host using MSBTS_ServerHost class  
   Set objServerHost = objService.Get ("MSBTS_ServerHost")  
  
   Set objSH = objServerHost.SpawnInstance_  
  
   objSH.HostName = HostName  
   objSH.ServerName = ServerName  
  
   ' Invoke MSBTS_ServerHost Map method  
   objSH.Map  
  
   CheckWMIError  
   wscript.echo "Host - " & HostName & " - has been mapped successfully to server - " & ServerName  
  
   ' Step 2 - Install the host instance using MSBTS_HostInstance class  
   Set objHostInstance = objService.Get ("MSBTS_HostInstance")  
  
   Set objHI = objHostInstance.SpawnInstance_  
  
   objHI.Name = "Microsoft BizTalk Server " & HostName & " " & ServerName  
  
   ' Invoke MSBTS_HostInstance Install method  
   objHI.Install uid, pwd, true   ' Calling MSBTS_HostInstance::Install(string Logon, string Password, boolean GrantLogOnAsService) method  
  
   CheckWMIError  
   wscript.echo "HostInstance - " & HostName & " - has been installed successfully on server - " & ServerName  
  
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

