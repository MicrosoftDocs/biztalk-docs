---
title: "How to Configure an IPDLC Link Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2363e1e2-86a8-4940-8ee4-e120a6832052
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure an IPDLC Link Service
### To configure an IPDLC link service  
  
1. Retrieve the command prompt instructions.  
  
2. If necessary, retrieve the adapter name.  
  
3. Create the link service.  
  
4. Create the independent session.  
  
   The following code sample describes how to configure an IPDLC link service. The following table describes the relevant command prompt switches:  
  
|Command line switch|Description|  
|-------------------------|-----------------|  
|**-p**|PrimaryNNS: the Primary Network Node Server|  
|**-b**|(Optional) BackupNNS: Backup Network Node Server|  
|**-d**|(Optional) device: Overrides the adapter name discovered|  
|**-l**|(Optional) LenNode: Used to configure the LEN node (default is 1st)|  
  
```  
    On Error Resume   Next  
'Declarations and Constants  
    Dim strPrimaryNNS  
    Dim strBackupNNS  
    Dim strLocalAddress  
    Dim strLenNode  
    Dim strComputerName  
    Dim wshEnvProc  
'Defaults  
    strPrimaryNNS = ""  
    strBackupNNS = ""  
    strLocalAddress = ""  
    strLenNode = "SNA Service"  
'Get the command line  
    Set objArgs = WScript.Arguments  
    For I = 0 to objArgs.Count - 1  
       select case objArgs(I)  
        Case "-p"  
            I = I + 1  
            strPrimaryNNS = objArgs(I)  
        case "-b"  
            I = I + 1  
            strBackupNNS = objArgs(I)  
        case "-d"  
            I = I + 1  
            strLocalAddress = objArgs(I)  
        case "-l"  
            I = I + 1  
            strLenNode = objArgs(I)  
        case else  
            Wscript.Echo "Script Usage: "  
            Wscript.Echo " -p Primary NNS (Required)"  
            Wscript.Echo " -b Backup NNS (Optional)"  
            wscript.echo " -d Device Name (Optional)"  
            wscript.echo " -l Len Node (Optional)"  
            return  
       end select  
    Next  
'NNS parameter is required  
    if strPrimaryNNS = "" then  
       Wscript.Echo "Please supply the -p (PrimaryNNS) parameter"  
       return  
    end if  
'See if we need to get a device  
    if strLocalAddress = "" then  
       GetAdapterName()  
    end if  
' Two methods for creating the link service and independent session connection  
    CreateIPDLCLinkService  
    CreateIndependentSession  
  
```