---
title: "How To Use REOverride to Specify a Remote Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46eef5d7-0e21-4baa-b45a-1317f963a3db
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How To Use REOverride to Specify a Remote Environment
To programmatically specify an RE, the application uses the managed context entry.  The context property must be set to true  on the method from within designer.  
  
 The following Visual Basic code shows an example virtually creating an RE within the application.  
  
```  
' You must set the following references in your project:   
'    Microsoft.HostIntegration.TI.ClientContext.dll  
'    Microsoft.HostIntegration.TI.Globals.dll  
  
Imports Microsoft.HostIntegration.TI  
  
 Dim TIContext As New ClientContext  
 Dim DynamicRE As ELMLinkRemoteEnvironment  
  
  DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.ELMLink, "MyRE")  
   DynamicRE.IPAddress = SystemAddress  
   DynamicRE.TCPPorts = PortNumber  
   TIContext.DynamicRE = DynamicRE  
  
Obj.Method1 parm1, parm2, parm3, TIContext  
  
```  
  
 The following Visual Basic code shows an example of HTTP using MSHMIRS.  
  
```  
Dim DynamicRE As HTTPLinkRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.HttpLink, "MyRE")  
DynamicRE.IPAddress = SystemAddress  
DynamicRE.HttpPort = PortNumber  
DynamicRE.MirrorProgramName = "MSHMIRS"  
DynamicRE.AliasTransactionId = "CWBA"  
TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of HTTP user data.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As HTTPUserDataRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.HttpUserData, "MyRE")  
DynamicRE.IPAddress = SystemAddress  
DynamicRE.HttpPort = PortNumber  
DynamicRE.AliasTransactionId = "CWBA"  
TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of CICS Link.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As SNALinkRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.SNALink, "MyRE")  
DynamicRE.LocalLUName = LocalLUName  
DynamicRE.RemoteLUName = RemoteLUName  
DynamicRE.ModeName = Mode  
TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of CICS LU6.2 user data.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As SNAUserDataRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.SNAUserData, "MyRE")  
DynamicRE.LocalLUName = LocalLUName  
DynamicRE.RemoteLUName = RemoteLUName  
DynamicRE.ModeName = Mode  
  
TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of IMS LU 6.2.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As SNAUserDataRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.IMSLU62, "MyRE")  
DynamicRE.LocalLUName = LocalLUName  
DynamicRE.RemoteLUName = RemoteLUName  
DynamicRE.ModeName = Mode  
TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of ELM Link.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As ELMLinkRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.ELMLink, "MyRE")  
DynamicRE.IPAddress = SystemAddress  
DynamicRE.TCPPorts = PortNumber  
TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of TRM Link with Security.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As TRMLinkRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.TRMLink, "MyRE")  
DynamicRE.IPAddress = SystemAddress  
DynamicRE.TCPPorts = PortNumber  
DynamicRE.Security = RemoteEnvironmentSecurity.User  
TIContext.DynamicRE = DynamicRE  
TIContext.User = "UserId"  
TIContext.Password = "Password"  
  
```  
  
 The following Visual Basic code shows an example of TRM user data with Security.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As TRMUserDataRemoteEnvironment  
  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.TRMUserData, "MyRE")  
DynamicRE.IPAddress = SystemAddress  
DynamicRE.TCPPorts = PortNumber  
DynamicRE.Security = RemoteEnvironmentSecurity.User  
TIContext.User = "UserId"  
TIContext.Password = "Password"  
TIContext.TransactionId = "CICS Transaction name"  
TIContext.DynamicRE = DynamicRE  
```  
  
 The following Visual Basic code shows an example of IMS Connect without security, exit HWSIMSO0.  
  
```  
Dim TIContext As New ClientContext  
 Dim DynamicRE As IMSConnectRemoteEnvironment  
  
 DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.IMSConnect, "MyRE")  
 DynamicRE.IPAddress = SystemAddress  
 DynamicRE.TCPPorts = PortNumber  
 DynamicRE.ItocExitName = "*IRMREQ*"  
 DynamicRE.OtmaSystemId = "IMS system ID"  
 TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of IMS Connect with security, exit HWSIMSO1.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As IMSConnectRemoteEnvironment  
  
 DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.IMSConnect, "MyRE")  
 DynamicRE.IPAddress = SystemAddress  
 DynamicRE.TCPPorts = PortNumber  
 DynamicRE.ItocExitName = "*IRMRE1*"  
 DynamicRE.OtmaSystemId = "IMS system ID"  
 DynamicRE.Security = RemoteEnvironmentSecurity.Off Or RemoteEnvironmentSecurity.ImsHWS01SecurityExit  
 TIContext.DynamicRE = DynamicRE  
  
```  
  
 The following Visual Basic code shows an example of OS 400 with security and library name.  
  
```  
Dim TIContext As New ClientContext  
Dim DynamicRE As DPCRemoteEnvironment  
DynamicRE = RemoteEnvironmentClassFactory.MakeRemoteEnvironment(DynamicRemoteEnvironmentTypes.DistributedProgramCall, "MyRE")  
DynamicRE.IPAddress = SystemAddress  
DynamicRE.TCPPorts = PortNumber  
DynamicRE.Security = RemoteEnvironmentSecurity.User  
TIContext.User = "UserID"  
TIContext.Password = "Password"  
TIContext.LibraryName = "Library Name"  
TIContext.DynamicRE = DynamicRE  
  
```  
  
## See Also  
 [Specifying a Remote Environment Programmatically](../core/specifying-a-remote-environment-programmatically1.md)