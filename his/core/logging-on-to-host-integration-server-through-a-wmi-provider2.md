---
title: "Logging on to Host Integration Server Through a WMI Provider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ab927a6-09fa-4a00-90d9-2ebb7840a43a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Logging on to Host Integration Server Through a WMI Provider
The first step that you must perform when you create a WMI application or script is to log on to WMI and set the security for your application. You can perform this action either by using the **SWbemLocator** locator object, or with a moniker.  
  
### To connect to WMI using SWbemLocator  
  
1. Retrieve a locator object with a call to **CreateObject**.  
  
2. Log on to the namespace with a call to **ConnectServer**.  
  
3. Set the impersonation level with a call to **Security._ImpersonationLevel**.  
  
4. Implement your task.  
  
   The following code sample shows how to connect to WMI using **SWbemLocator**:  
  
```  
Set WmiLocator = CreateObject("WbemScripting.SWbemLocator")  
Set WmiNameSpace = WmiLocator.ConnectServer("","root\MicrosoftHIS","", "","", "",0,Nothing)  
  
if Err = 0 then  
    'Retrieve the SNA_LU_Lua class  
    Set ServerClass = WmiNamespace.Get("MsSNA_LuLua")  
    Set Path = ServerClass.Path_  
    ServerClass.Security_.impersonationLevel = 3  
    Set LU3270 = ServerClass.Instances_  
  
```  
  
 Another way you can connect to WMI is by using a moniker. A moniker is essentially a compact version of the above lines of code, and contains the WMI namespace and other connection information.  
  
#### To connect to WMI using a moniker  
  
1. Call **GetObject** with a moniker in the input parameter.  
  
2. Implement your task.  
  
   The following example shows how to connect to WMI using a moniker:  
  
```  
set objService = GetObject("winmgmts:root/microsofthis")  
  
```