---
description: "Learn more about: How to Retrieve an Adapter Name"
title: "How to Retrieve an Adapter Name2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Retrieve an Adapter Name
One of the tasks you must perform when setting up an IPDLC connection is to retrieve the name of the adapter you are connecting with.  
  
### To retrieve an adapter name  
  
1. Connect to the namespace on the local computer using **GetObject**.  
  
2. Retrieve the name of the adapter using **ExecMethod** with **GetAllNetworkAdapters** as the method to execute.  
  
   The following example shows how to retrieve the name of the first adapter on a system:  
  
```  
Private Sub GetAdapterName()  
   Dim objService, outParam, objSD, MyArray, nArray  
   set objService = GetObject("winmgmts:root/microsofthis")  
   set outParam = objService.Execmethod("MsSna_LinkService_IPDLC",   
"GetAllNetworkAdapters")  
   objSD = Join(outParam.Adapters, ",")  
   MyArray = Split(objSD, ",")  
   nArray = Ubound(MyArray)  
   if nArray < 0 then  
      strLocalAddress = ""  
   else  
      strLocalAddress = MyArray(0)  'default to first one  
   end if  
End Sub  
  
```
