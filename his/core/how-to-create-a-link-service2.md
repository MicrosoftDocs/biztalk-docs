---
title: "How to Create a Link Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbb682f6-41a6-49da-a89b-da6f6bca5989
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Create a Link Service
Another task you may want to perform when setting up an IPDLC connection is to create the link service.  
  
### To create a link service  
  
1. Connect to the namespace on the local computer using **GetObject**.  
  
2. Create the new link service instance using **SpawnInstance**.  
  
3. Set the properties of the new link service.  
  
4. Commit the new instance to memory using the **Put_** method.  
  
   The following example shows how to create a new link service:  
  
```  
private Sub CreateIPDLCLinkService  
    on error resume next  
' Connect to the namepsace on the local machine  
    Set Namespace = GetObject("Winmgmts:root\MicrosoftHIS")  
    Set ObjClass  = Namespace.Get("MsSna_LinkService_IpDlc")     
' Create new link service instance  
    Set NewInst   = ObjClass.SpawnInstance_  
    ' Set instance properties  
    NewInst.NetworkName = Left(strComputerName, 8)  
    NewInst.CPName = "IPDLCLS"  
    NewInst.NodeID = "05D.FFFFF"  
    NewInst.AddressType = 2  
    NewInst.LocalAddress = Trim(strLocalAddress)  
    NewInst.LENNode = strLenNode  
    NewInst.PrimaryNNS = strPrimaryNNS  
    if (strBackupNNS <> Empty) then  
        NewInst.BackupNNS = strBackupNNS  
    end if  
    ' Commit the instance  
    NewInst.Put_  
    if Err.Number <> 0 then  
        PrintWMIErrorThenExit Err.Description, Err.Number  
        Wscript.Echo "Link Service Creation Failed " & Err.Description  
    Else   
        Wscript.Echo "Link Serice Created Successfully"  
    end if  
End Sub  
  
```