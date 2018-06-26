---
title: "How to Display Connection Status1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3cf7466-d961-4493-97a8-5aad77c9b5c2
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Display Connection Status
Retrieving the status of a connection is a common task that you might want to perform with WMI.  
  
### To display the status of a connection  
  
1. Connect to the namespace using **GetObject** with a moniker in the parameter.  
  
2. Enumerate **MsSnaStatus_Connections** using **ExecQuery**.  
  
3. Display error codes if necessary.  
  
   The following example shows how to display the status of all the connections defined in Host Integration Server (HIS):  
  
```  
Private Function DisplayConnectionStatus ()  
'Variables  
   Dim objWMIService, colItems, iCounter, objItem, _  
       strReport  
'Connect to the namespace  
   Set objWMIService = GetObject("winmgmts:\\" & strComputer & "\root\microsofthis")  
'Enumerate the Class  
   Set colItems = objWMIService.ExecQuery("Select * from MSSnaStatus_Connection")  
   iCounter = colItems.Count  
   if Err.Number = 0 then  
      For Each objItem in colItems  
         strReport = "Connection " & objItem.Name & " status is " & objItem.StatusText     
         Wscript.Echo strReport  
         strReport = ""        
      Next  
   else  
      Wscript.Echo "An error occurred enumerating instances for status " & Err.Number & " " & Err.Description  
   End If  
   DisplayConnectionStatus = true  
End Function  
  
```