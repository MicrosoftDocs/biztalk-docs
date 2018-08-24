---
title: Listening for a Suspended Event Using WMI
TOCTitle: Listening for a Suspended Event Using WMI
ms:assetid: 921444a0-16df-4c7a-8029-9377c367c018
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577357(v=BTS.80)
ms:contentKeyID: 51529724
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- csharp
---

# Listening for a Suspended Event Using WMI

 

Use the following code to listen for a [MSBTS\_ServiceInstanceSuspendedEvent](msbts-serviceinstancesuspendedevent-wmi.md).

``` csharp
using System.Management;  
  
      static public void ListenForSvcInstSuspendEvent()  
      {  
         try  
         {  
            // Set up an event watcher and a handler for the MSBTS_ServiceInstanceSuspendedEvent event  
            ManagementEventWatcher watcher = new ManagementEventWatcher( new ManagementScope("root\\MicrosoftBizTalkServer"),  
               new EventQuery("SELECT * FROM MSBTS_ServiceInstanceSuspendedEvent") );  
  
            watcher.EventArrived += new EventArrivedEventHandler(MyEventHandler);  
  
            // Start watching for MSBTS_ServiceInstanceSuspendedEvent events  
            watcher.Start();  
  
            while (true)  
            {  
               System.Threading.Thread.Sleep(1000);  
            }  
         }  
         catch (Exception excep)  
         {  
            Console.WriteLine("Error: " + excep.Message);  
         }  
      }  
  
      static public void MyEventHandler(object sender, EventArrivedEventArgs e)   
      {  
         // Print out the service instance ID and error description upon receiving of the suspend event  
         Console.WriteLine("A MSBTS_ServiceInstanceSuspendEvent has occurred!");  
         Console.WriteLine(string.Format("ServiceInstanceID: {0}", e.NewEvent["InstanceID"]));  
         Console.WriteLine(string.Format("ErrorDescription: {0}", e.NewEvent["ErrorDescription"]));  
         Console.WriteLine("");  
      }  
```

``` 
Option Explicit  
  
Sub ListenForSvcInstSuspendEvent()  
  
   Set objWMIServices = GetObject("WinMgmts:{impersonationLevel=impersonate, (security)}\\.\root\MicrosoftBizTalkServer")   
  
   ' Create the event sink object that receives the events  
   Set sinkSuspInst = WScript.CreateObject("WbemScripting.SWbemSink","SINK_INST_")  
  
   ' Set up the event selection. SINK_INST_OnObjectReady is called when a MSBTS_ServiceInstanceSuspendedEvent occurs  
   objWMIServices.ExecNotificationQueryAsync sinkSuspInst, "select * from MSBTS_ServiceInstanceSuspendedEvent"  
  
   ' Infinite loop to wait for event to happen  
   wscript.echo "Waiting for events..."  
   while(true)  
      WScript.Sleep(1000)  
   wend  
End Sub  
  
Sub SINK_INST_OnObjectReady(objObject, objAsyncContext)  
   wscript.echo "=============================================="  
   wscript.echo "A MSBTS_ServiceInstanceSuspendEvent has occurred!"  
   wscript.echo ""  
   wscript.echo "ServiceInstanceID: " & objObject.InstanceID  
   wscript.echo ""  
   wscript.echo "ErrorDescription: " & objObject.ErrorDescription  
   wscript.echo ""  
End Sub  
```

## See Also

[WMI Script Samples](wmi-script-samples.md)  
[MSBTS\_ServiceInstanceSuspendedEvent (WMI)](msbts-serviceinstancesuspendedevent-wmi.md)

