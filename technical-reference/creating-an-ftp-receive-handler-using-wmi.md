---
title: Creating an FTP Receive Handler Using WMI
TOCTitle: Creating an FTP Receive Handler Using WMI
ms:assetid: 54bbf495-866b-4d3f-a1b7-db256a9bcff7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560206(v=BTS.80)
ms:contentKeyID: 51528100
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Creating an FTP Receive Handler Using WMI

 

Use the following code to create an FTP receive handler instance with the [CustomCfg](msbts-receivehandler-customcfg-property-wmi.md) property of the [MSBTS\_ReceiveHandler](msbts-receivehandler-wmi.md) class.

``` csharp
using System.Management;  
  
      //Sample to show MSBTS_ReceiveHandler instance creation with CustomCfg property  
      public void CreateFTPReceiveHandler(string HostName)  
      {  
         string AdapterName = "FTP";   //Assume FTP adapter name is named as default value "FTP"  
         try  
         {  
            PutOptions options = new PutOptions();   
            options.Type = PutType.CreateOnly;  
  
            //create a ManagementClass object and spawn a ManagementObject instance  
            ManagementClass objReceiveHandlerClass = new ManagementClass("root\\MicrosoftBizTalkServer", "MSBTS_ReceiveHandler", null);  
            ManagementObject objReceiveHandler  = objReceiveHandlerClass.CreateInstance();  
  
            //set the properties for the Managementobject  
            objReceiveHandler["AdapterName"] = AdapterName;  
            objReceiveHandler["HostName"] = HostName;  
            objReceiveHandler["CustomCfg"] = "<CustomProps><AdapterConfig vt=\"8\"><Config xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\" xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\"><userName>Username</userName><password>Password</password><accountName>FTP Account</accountName><representationType>binary</representationType><spoolingFolder>c:\\Temp</spoolingFolder><maximumBatchSize>10</maximumBatchSize><maximumNumberOfFiles>10</maximumNumberOfFiles><passiveMode>False</passiveMode><beforeGet>BeforeGet</beforeGet><afterGet>AfterGet</afterGet><firewallType>NoFirewall</firewallType><firewallAddress>FireWallAddress</firewallAddress><firewallPort>21</firewallPort><firewallUserName>Username</firewallUserName><firewallPassword>Password</firewallPassword><commandLogFilename>c:\\Log</commandLogFilename><errorThreshold>10</errorThreshold><maxFileSize>100</maxFileSize></Config></AdapterConfig></CustomProps>";  
  
            //create the Managementobject  
            objReceiveHandler.Put(options);  
            System.Console.WriteLine("ReceiveHandler - " + AdapterName + " " + HostName + " - has been created successfully");  
         }  
         catch(Exception excep)  
         {  
            System.Console.WriteLine("CreateReceiveHandler - " + AdapterName + " " + HostName + " - failed: " + excep.Message);  
         }  
      }  
```

``` 
Option Explicit  
  
' wbemChangeFlagEnum Setting  
const CreateOnly = 2  
  
' Sample to show MSBTS_ReceiveHandler instance creation with CustomCfg property  
Sub CreateFTPReceiveHandler (HostName)  
   On Error Resume Next  
  
   Dim objLocator, objService, objReceiveHandler, objRH, AdapterName  
   AdapterName = "FTP"   ' Assume FTP Adapter is named as the default value "FTP"  
  
   ' Connects to local server WMI Provider BizTalk namespace  
   Set objLocator = Createobject ("wbemScripting.SWbemLocator")  
   Set objService = objLocator.ConnectServer(".", "root/MicrosoftBizTalkServer")  
  
   ' Get WMI class MSBTS_ReceiveHandler  
   Set objReceiveHandler = objService.Get ("MSBTS_ReceiveHandler")  
  
   Set objRH = objReceiveHandler.SpawnInstance_  
  
   objRH.AdapterName = AdapterName  
   objRH.HostName = HostName  
   objRH.CustomCfg = "<CustomProps><AdapterConfig vt=""8""><Config xmlns:xsd=""http://www.w3.org/2001/XMLSchema"" xmlns:xsi=""http://www.w3.org/2001/XMLSchema-instance""><userName>Username</userName><password>Password</password><accountName>FTP Account</accountName><representationType>binary</representationType><spoolingFolder>c:\Temp</spoolingFolder><maximumBatchSize>10</maximumBatchSize><maximumNumberOfFiles>10</maximumNumberOfFiles><passiveMode>False</passiveMode><beforeGet>BeforeGet</beforeGet><afterGet>AfterGet</afterGet><firewallType>NoFirewall</firewallType><firewallAddress>FireWallAddress</firewallAddress><firewallPort>21</firewallPort><firewallUserName>Username</firewallUserName><firewallPassword>Password</firewallPassword><commandLogFilename>c:\Log</commandLogFilename><errorThreshold>10</errorThreshold><maxFileSize>100</maxFileSize></Config></AdapterConfig></CustomProps>"  
  
   ' Create instance  
   objRH.Put_(CreateOnly)  
  
   CheckWMIError  
   wscript.echo "Receive Handler - " & AdapterName & " " & HostName & " - has been created successfully"  
  
end Sub  
  
'This subroutine deals with all errors using the WbemScripting object.  Error descriptions  
'are returned to the user by printing to the console.  
Sub   CheckWMIError()  
  
   If Err <> 0 Then  
      On Error Resume Next  
  
      Dim strErrDesc: strErrDesc = Err.Description  
      Dim ErrNum: ErrNum = Err.Number  
      Dim WMIError : Set WMIError = CreateObject("WbemScripting.SwbemLastError")  
  
      If ( TypeName(WMIError) = "Empty" ) Then  
         wscript.echo strErrDesc & " (HRESULT: "& Hex(ErrNum) & ")."  
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
[MSBTS\_ReceiveHandler (WMI)](msbts-receivehandler-wmi.md)  
[Configuring the FTP Adapter](https://msdn.microsoft.com/en-us/library/aa561032\(v=bts.80\))

