---
title: "How to Create an Independent Session1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 086f92f8-f69a-4166-bb25-dbec2565ebba
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Create an Independent Session
After you have created the link service, you need to create an independent session to use.  
  
## To create an independent session  
  
1. Create the "Independent Sessions Connection" record.  
  
2. Validate that the session was created.  
  
3. Define the properties of the new connection.  
  
   The following code sample shows how to create an independent session:  
  
```  
Private Sub CreateIndependentSession  
    On error resume next  
'Create the Independent Sessions Connection record.  
    Set Namespace = GetObject("Winmgmts:root\MicrosoftHIS")  
'Validate that the instance was created  
    strQuery = "select * from MsSna_LinkService_IpDlc"  
    ' this is our instance  
    Set instset = Namespace.ExecQuery(strQuery)  
    if ( instset.Count<>1) Then  
        wscript.echo "No instances found for the link service query " & strQuery  
    End If  
    For each inst_ in instSet  
        Set Inst = inst_ ' This is our new instance  
    Next ' end of query workaround     
    ' define independent sessions connection  
    Set ObjClass = Namespace.Get("MsSna_ConnectionIpDlc")  
    Set IndepConn = ObjClass.SpawnInstance_  
    IndepConn.Activation = 0  
    IndepConn.Adapter = "SNAIP1"  
    IndepConn.AllowIncoming = TRUE  
    IndepConn.BackupDLUSCPName = ""  
    IndepConn.BackupDLUSNetName = ""  
    IndepConn.BlockId = "05D"  
    IndepConn.Comment = ""  
    IndepConn.CompressionLevel = 0  
    IndepConn.DLURRetryDelay = 0  
    IndepConn.DLURRetryLimit = 0  
    IndepConn.DLURRetryType = 0  
    IndepConn.DynamicLuDef = TRUE  
    IndepConn.IndepSess = TRUE  
    IndepConn.LocalControlPoint = ""  
    IndepConn.LocalNetName = ""  
    IndepConn.Name = Inst.Name  
    IndepConn.NodeId = "FFFFF"  
    IndepConn.PartnerConnectionName = ""  
    IndepConn.PeerRole = 1  
    IndepConn.PrimDLUSCPName = ""  
    IndepConn.PrimDLUSNetName = ""  
    IndepConn.RemoteAddress = ""  
    IndepConn.RemoteBlockId = ""  
    IndepConn.RemoteControlPoint = ""  
    IndepConn.RemoteEnd = 1  
    IndepConn.RemoteNetName = ""  
    IndepConn.RemoteNodeId = ""  
    IndepConn.RetryDelay = 0  
    IndepConn.RetryLimit = 0  
    IndepConn.Service = strComputerName  
    IndepConn.XIDFormat = 1  
    IndepConn.Put_  
    if Err.Number <> 0 then  
        PrintWMIErrorThenExit Err.Description, Err.Number  
    End If  
End Sub  
  
```  
  
## See Also  
[How to Create a Link Service](../core/how-to-create-a-link-service2.md)