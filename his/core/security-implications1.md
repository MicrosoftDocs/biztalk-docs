---
title: "Security Implications1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 270c33d8-9671-4a0e-933e-32c3e9fab2b8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Security Implications
Transaction Integrator (TI) can provide user ID and password credentials for authentication on the mainframe. They are provided in compliance with existing IBM standards, and mainframe authentication is completed by standard IBM procedures such as Resource Access Control Facility (RACF), Top Secret, and so on. All mainframe authentication is completed in a manner transparent to the developer.  
  
 When LU 6.2 is used for connectivity, credentials are transmitted to the mainframe in an SNA LU 6.2 Function Management Header Type 5 (FMH-5) ATTACH message. For more information, refer to the IBM manual, *Systems* *Network* *Architecture* *Formats,* *Document* *Number* *GA27-3136-16,* *Section* *11.1.5* *FM* *Header* *5:* *Attach* *(LU* *6.2*).  
  
 When TCP/IP is used for connectivity, credentials are transmitted in the Transaction Request Message (TRM) sent from TI to the Listener. There are some additional coding requirements on the mainframe for TCP/IP to provide user exits for authentication. For information about CICS, refer to *IBM* *TCP/IP* *for* *MVS* *CICS* *TCP/IP* *Socket* *Interface* *Guide* *and* *Reference,* *Document* *Number* *SC31-7131-03,* *Section* *6.6.3* *Writing* *Your* *Own* *Security* *Link* *Module* *for* *the* *Listener*. For information about IMS, refer to *IBM* *TCP/IP* *for* *MVS* *IMS* *TCP/IP* *Application* *Development* *Guide* *and* *Reference,* *Document* *Number* *SC31-7186-03,* *Section* *3.4.4* *The* *IMS* *Listener* *Security* *Exit*. Prior to TCP/IP version 3R2, the CICS exit module required the name, EZACICSE. However, you can choose any name when you are using TCP/IP version 3R2. For IMS, the exit module must be named IMSLSECX.  
  
 There are three alternative sources of mainframe credentials.  
  
- The identity of the COM+ application that contains the TI component.  
  
- The identity of the Windows user of the TI application.  
  
- The optional explicit security override feature of TI.  
  
  Use of the explicit override feature dissociates mainframe security from Windows security; therefore, its use is not recommended over the first two alternatives. Using either of the first two alternatives integrates mainframe security with Windows security by using [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Enterprise Single Sign-On (ESSO) functionality.  
  
  By default, passing credentials to the mainframe for authentication is not enabled. You must activate the TI remote environment (RE) security properties by selecting the **Set security on** check box. You must click either **Authenticate with package credentials** or **Authenticate with user credentials** even if you plan to use the explicit security override feature.  
  
  To select the explicit security override, select the **Allow application override** check box. This option is the least recommended of the three. If **Allow application override** is selected but not implemented by the application, the security mechanism reverts to whichever of the other two security options you selected.  
  
> [!NOTE]
>  Explicit security override is not the preferred method of specifying credentials for a client. If possible, you should use the Client Context USERID and PASSWORD override keywords. For more information, see the [COMTIContext Keywords](./comticontext-keywords1.md).  
  
## In This Section  
 [How to Use Optional Explicit-Level Override Authentication](../core/how-to-use-optional-explicit-level-override-authentication1.md)  
  
 [Level of Security](../core/level-of-security1.md)  
  
 [How to Use Already Verified Authentication](../core/how-to-use-already-verified-authentication2.md)  
  
 [Mainframe Authentication for CICS LINREs](../core/mainframe-authentication-for-cics-linres1.md)