---
title: "How to Retrieve Connection Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 517ae082-6425-4ce1-84bb-54ac0731ac84
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Retrieve Connection Information
Another common task you may want to perform with Windows Management Instrumentation (WMI) for Host Integration Server is retrieving information regarding a connection.  
  
### To retrieve connection information  
  
1. Connect to the namespace using **GetObject** with a moniker in the parameter.  
  
2. Retrieve all connection information objects using **ExecQuery**.  
  
3. Display the information as appropriate.  
  
   The following code sample shows how to retrieve information about an SDLC connection:  
  
```  
On Error Resume Next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:\\" & strComputer & "\root\MicrosoftHIS")  
Set colItems = objWMIService.ExecQuery("Select * from MsSna_ConnectionSdlc",,48)  
For Each objItem in colItems  
    Wscript.Echo "Activation: " & objItem.Activation  
    Wscript.Echo "Adapter: " & objItem.Adapter  
    Wscript.Echo "AllowIncoming: " & objItem.AllowIncoming  
    Wscript.Echo "BlockId: " & objItem.BlockId  
    Wscript.Echo "Comment: " & objItem.Comment  
    Wscript.Echo "CompressionLevel: " & objItem.CompressionLevel  
    Wscript.Echo "DialData: " & objItem.DialData  
    Wscript.Echo "DynamicLuDef: " & objItem.DynamicLuDef  
    Wscript.Echo "LocalControlPoint: " & objItem.LocalControlPoint  
    Wscript.Echo "LocalNetName: " & objItem.LocalNetName  
    Wscript.Echo "MaxBtu: " & objItem.MaxBtu  
    Wscript.Echo "Name: " & objItem.Name  
    Wscript.Echo "NodeId: " & objItem.NodeId  
    Wscript.Echo "PartnerConnectionName: " & objItem.PartnerConnectionName  
    Wscript.Echo "PeerRole: " & objItem.PeerRole  
    Wscript.Echo "RemoteBlockId: " & objItem.RemoteBlockId  
    Wscript.Echo "RemoteControlPoint: " & objItem.RemoteControlPoint  
    Wscript.Echo "RemoteEnd: " & objItem.RemoteEnd  
    Wscript.Echo "RemoteNetName: " & objItem.RemoteNetName  
    Wscript.Echo "RemoteNodeId: " & objItem.RemoteNodeId  
    Wscript.Echo "RetryDelay: " & objItem.RetryDelay  
    Wscript.Echo "RetryLimit: " & objItem.RetryLimit  
    Wscript.Echo "SdlcContactLimit: " & objItem.SdlcContactLimit  
    Wscript.Echo "SdlcContactTO: " & objItem.SdlcContactTO  
    Wscript.Echo "SdlcDataRate: " & objItem.SdlcDataRate  
    Wscript.Echo "SdlcDuplex: " & objItem.SdlcDuplex  
    Wscript.Echo "SdlcEncoding: " & objItem.SdlcEncoding  
    Wscript.Echo "SdlcIdleLimit: " & objItem.SdlcIdleLimit  
    Wscript.Echo "SdlcIdleTO: " & objItem.SdlcIdleTO  
    Wscript.Echo "SdlcLeasedLine: " & objItem.SdlcLeasedLine  
    Wscript.Echo "SdlcMultiPrimary: " & objItem.SdlcMultiPrimary  
    Wscript.Echo "SdlcPollAddress: " & objItem.SdlcPollAddress  
    Wscript.Echo "SdlcPollLimit: " & objItem.SdlcPollLimit  
    Wscript.Echo "SdlcPollRate: " & objItem.SdlcPollRate  
    Wscript.Echo "SdlcPollTO: " & objItem.SdlcPollTO  
    Wscript.Echo "SdlcStandby: " & objItem.SdlcStandby  
    Wscript.Echo "SdlcSwitchTO: " & objItem.SdlcSwitchTO  
    Wscript.Echo "Service: " & objItem.Service  
    Wscript.Echo "StatusText: " & objItem.StatusText  
    Wscript.Echo "XIDFormat: " & objItem.XIDFormat  
Next  
  
```