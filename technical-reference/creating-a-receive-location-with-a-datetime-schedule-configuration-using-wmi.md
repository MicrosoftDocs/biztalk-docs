---
title: Creating a Receive Location with a Datetime Schedule Configuration Using WMI
TOCTitle: Creating a Receive Location with a Datetime Schedule Configuration Using WMI
ms:assetid: 3257d7f4-78e9-4862-9517-1468a8efa6c4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559496(v=BTS.80)
ms:contentKeyID: 51527225
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Creating a Receive Location with a Datetime Schedule Configuration Using WMI

 

Use the following code to create an [MSBTS\_ReceiveLocation](msbts-receivelocation-wmi.md) with a datetime schedule configuration.

``` csharp
using System.Management;  
  
      //Sample to show MSBTS_ReceiveLocation instance creation with Date/Time schedule config  
      public void CreateReceiveLocation (string AdapterName, string ReceiveLocationName, string ReceivePortName, string HostName, string InboundTransportURL)  
      {  
         try  
         {  
            PutOptions options = new PutOptions();   
            options.Type = PutType.CreateOnly;  
  
            //Step1 - Create a Receive Port  
            //create a ManagementClass object and spawn a ManagementObject instance  
            ManagementClass objReceivePortClass = new ManagementClass("root\\MicrosoftBizTalkServer", "MSBTS_ReceivePort", null);  
            ManagementObject objReceivePort  = objReceivePortClass.CreateInstance();  
  
            //set the properties for the Managementobject  
            objReceivePort["Name"] = ReceivePortName;  
            objReceivePort["IsTwoWay"] = false;  
  
            //create the Managementobject  
            objReceivePort.Put(options);  
            System.Console.WriteLine("ReceivePort - " + ReceivePortName + " - has been created successfully");  
  
            //Step2 - Create a Receive Location to associate a Receive Port  
            //create a ManagementClass object and spawn a ManagementObject instance  
            ManagementClass objReceiveLocationClass = new ManagementClass("root\\MicrosoftBizTalkServer", "MSBTS_ReceiveLocation", null);  
            ManagementObject objReceiveLocation  = objReceiveLocationClass.CreateInstance();  
  
            //set the properties for the Managementobject  
            objReceiveLocation["Name"] = ReceiveLocationName;  
            objReceiveLocation["ReceivePortName"] = ReceivePortName;  
            objReceiveLocation["AdapterName"] = AdapterName;  
            objReceiveLocation["InboundTransportURL"] = InboundTransportURL;  
            objReceiveLocation["HostName"] = HostName;  
            objReceiveLocation["PipelineName"] = "Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
            objReceiveLocation["StartDateEnabled"] = true;   // Enable schedule start date  
            objReceiveLocation["ActiveStartDT"] = "20040301000000.000000-480";   // Set start Date as March 1st, 2004  
            objReceiveLocation["StopDateEnabled"] = true;   // Enable schedule stop date  
            objReceiveLocation["ActiveStopDT"] = "20040630010000.000000-420";   // Set stop date as June 30th, 2004  
            objReceiveLocation["OperatingWindowEnabled"] = true;   // Enable operating window  
            objReceiveLocation["SrvWinStartDT"] = "20000101080000.000000-480";   // Set start time as Pacific Time 8:00 am  
            objReceiveLocation["SrvWinStopDT"] = "20000101213000.000000-480";   // Set stop time as Pacific Time 9:30 pm  
  
            //create the Managementobject  
            objReceiveLocation.Put(options);  
            System.Console.WriteLine("ReceiveLocation - " + ReceiveLocationName + " - has been created successfully");  
         }  
         catch(Exception excep)  
         {  
            System.Console.WriteLine("CreateReceiveLocation - " + ReceiveLocationName + " - failed: " + excep.Message);  
         }  
      }  
```

``` VBScript
Option Explicit  
  
' wbemChangeFlagEnum Setting  
const UpdateOnly = 1  
  
' Sample to show MSBTS_ReceiveLocation instance creation with Date/Time schedule config  
Sub CreateReceiveLocation (AdapterName, ReceiveLocationName, ReceivePortName, HostName, InboundTransportURL)  
   On Error Resume Next  
  
   Dim objLocator, objService, objReceivePort, objRP, objReceiveLocation, objRL  
  
   ' Connects to local server WMI Provider BizTalk namespace  
   Set objLocator = Createobject ("wbemScripting.SWbemLocator")  
   Set objService = objLocator.ConnectServer(".", "root/MicrosoftBizTalkServer")  
  
   ' Step 1 - Create a Receive Port  
   ' Get WMI class MSBTS_ReceivePort  
   Set objReceivePort = objService.Get ("MSBTS_ReceivePort")  
  
   Set objRP = objReceivePort.SpawnInstance_  
  
   objRP.Name = ReceivePortName  
   objRP.IsTwoWay = false  
  
   ' Create instance  
   objRP.Put_(CreateOnly)  
  
   CheckWMIError  
   wscript.echo "Receive Port - " & ReceivePortName & " - has been created successfully"  
  
   ' Step 2 - Create a Receive Location to associate a Receive Port  
   ' Get WMI class MSBTS_ReceiveLocation  
   Set objReceiveLocation = objService.Get ("MSBTS_ReceiveLocation")  
  
   Set objRL = objReceiveLocation.SpawnInstance_  
  
   objRL.Name = ReceiveLocationName  
   objRL.ReceivePortName = ReceivePortName  
   objRL.AdapterName = AdapterName  
   objRL.InboundTransportURL = InboundTransportURL  
   objRL.HostName = HostName  
   objRL.PipelineName="Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  
   objRL.StartDateEnabled = true   ' Enable schedule start date  
   objRL.ActiveStartDT = "20040301000000.000000-480"   ' Set start Date as March 1st, 2004  
   objRL.StopDateEnabled = true   ' Enable schedule stop date  
   objRL.ActiveStopDT = "20040630010000.000000-420"   ' Set stop date as June 30th, 2004  
   objRL.OperatingWindowEnabled = true   ' Enable operating window  
   objRL.SrvWinStartDT = "20000101080000.000000-480"   ' Set start time as Pacific Time 8:00 am  
   objRL.SrvWinStopDT = "20000101213000.000000-480"   ' Set stop time as Pacific Time 9:30 pm  
  
   ' Create instance  
   objRL.Put_(CreateOnly)  
  
   CheckWMIError  
   wscript.echo "Receive Location - " & ReceiveLocationName & " - has been created successfully"  
  
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
[MSBTS\_ReceiveLocation (WMI)](msbts-receivelocation-wmi.md)  
[MSBTS\_ReceivePort (WMI)](msbts-receiveport-wmi.md)

