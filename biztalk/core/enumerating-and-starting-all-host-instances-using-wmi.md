---
title: "Enumerating and Starting All Host Instances Using WMI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d580d161-b282-40bc-af51-8f6d2c10a471
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enumerating and Starting All Host Instances Using WMI
Use the following code to enumerate and start all host instances using the [MSBTS_HostInstance](../core/msbts-hostinstance-wmi.md) class.  
  
```csharp  
using System.Management;  
  
      //Function to Enumerate all HostInstances of "InProcess" type and start them  
      public void EnumerateAndStart()  
      {  
         try  
         {  
            //Create EnumerationOptions and run wql query  
            EnumerationOptions enumOptions = new EnumerationOptions();  
            enumOptions.ReturnImmediately = false;  
            //Search for all HostInstances of 'InProcess' type in the Biztalk namespace scope  
            ManagementObjectSearcher searchObject = new ManagementObjectSearcher("root\\MicrosoftBizTalkServer","Select * from MSBTS_HostInstance where HostType=1",enumOptions);  
  
            //Enumerate through the result set and start each HostInstance if it is already stopped  
            foreach(ManagementObject inst in searchObject.Get())  
            {  
               //Check if ServiceState is 'Stopped'  
               if(inst["ServiceState"].ToString() == "1")  
               {  
                  inst.InvokeMethod("Start",null);  
               }  
               Console.WriteLine("HostInstance of Host: " + inst["HostName"] + " and Server: " + inst["RunningServer"] + " was started successfully");  
            }  
  
            Console.WriteLine("All HostInstances started");  
            return;  
         }  
         catch(Exception excep)  
         {  
            Console.WriteLine("Failure while starting HostInstances - " + excep.Message);  
         }  
  
}  
```  
  
```vbs  
Option Explicit  
  
' Host Instance status number  
Const HostInstServiceState_Stopped = 1  
  
' Basic WMI operations - Enumerate and invoke method  
' Sample to show starting all host instance using MSBTS_HostInstance  
Sub StartAllInProcessHostInstance ()  
   On Error Resume Next  
  
   Dim Query, HostInstSet, Inst  
  
   ' Enumerate all InProcess type Host Instance  
   Query = "SELECT * FROM MSBTS_HostInstance WHERE HostType =1"  
   Set HostInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(Query)  
  
   For Each Inst in HostInstSet  
  
      ' If host instance is stopped, then it'll start it  
      If( HostInstServiceState_Stopped = Inst.ServiceState ) Then  
         wscript.echo "Starting host instance..."  
             Inst.Start   ' Calling MSBTS_HostInstance::Start() method  
         CheckWMIError  
         wscript.echo "HostInstance - " & Inst.HostName & " - has been started successfully on server - " & Inst.RunningServer  
      End If  
   Next  
  
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
 [MSBTS_HostInstance (WMI)](../core/msbts-hostinstance-wmi.md)