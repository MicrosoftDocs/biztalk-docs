---
title: "How to Capture a Trace with WMI1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b295b485-10de-4495-9ea2-45661f896258
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Capture a Trace with WMI
Trace capturing refers to the process of viewing trace logs. For Host Integration Server, this typically refers to collating data stored in trace log objects into a single file and saving it to a specified location. You can capture SNA trace information in the same manner as you would retrieve any other information from Windows Management Instrumentation (WMI). You use **ExecQuery** to make a call to the relevant object, and then write the information to the location you want.  
  
### To capture a trace  
  
1. Connect to the namespace using **GetObject** with a moniker in the parameter.  
  
2. Retrieve the objects representing the SNA Application using **ExecQuery**.  
  
    The core functionality of capturing a trace can be described in the following code:  
  
   ```  
   Set colItems = objWMIService.ExecQuery("Select * from MsHisTrace_SNAApplication",,48)  
   Set colItems = objWMIService.ExecQuery("Select * from MsHisTrace_SNABase",,48)  
   ```  
  
    Everything else in this sample is to support logging to a file.  
  
   The following code example shows how to capture a trace:  
  
```  
On Error Resume Next  
strComputer = "."  
Dim iCounter  
'Initialize  
    CreateLogFile  
    Set objWMIService = GetObject("winmgmts:\\" & strComputer & "\root\MicrosoftHIS")  
  
'Validate TraceSnaApplication  
    iCounter = 0  
    Set colItems = objWMIService.ExecQuery("Select * from MsHisTrace_SNAApplication",,48)  
For Each objItem in colItems  
    Wscript.Echo "APPCTrace: " & objItem.APPCTrace  
    Wscript.Echo "CPICTrace: " & objItem.CPICTrace  
    Wscript.Echo "CSVTrace: " & objItem.CSVTrace  
    Wscript.Echo "EnabledTraces: " & objItem.EnabledTraces  
    Wscript.Echo "InternalMessageTrace: " & objItem.InternalMessageTrace  
    Wscript.Echo "LU62Trace: " & objItem.LU62Trace  
    Wscript.Echo "LUATrace: " & objItem.LUATrace  
    Wscript.Echo "T3270Trace: " & objItem.T3270Trace  
    iCounter = iCounter + 1  
Next  
  
if iCounter > 0 then  
    Wscript.Echo "Number of Instances found " & iCounter  
else  
    Wscript.Echo "No Instances Found"  
End If  
  
    iCounter = 0  
    Set colItems = objWMIService.ExecQuery("Select * from MsHisTrace_SNABase",,48)  
For Each objItem in colItems  
    Wscript.Echo "EnabledTraces: " & objItem.EnabledTraces  
    Wscript.Echo "InternalMessageTrace: " & objItem.InternalMessageTrace  
    Wscript.Echo "LU62Trace: " & objItem.LU62Trace  
    Wscript.Echo "T3270Trace: " & objItem.T3270Trace  
    iCounter = iCounter + 1  
Next  
  
if iCounter > 0 then  
    Wscript.Echo "Number of Instances found " & iCounter  
else  
    Wscript.Echo "No Instances Found"  
End If  
  
```