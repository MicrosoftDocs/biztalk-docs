---
title: "How to Use the Trace Utility in Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "host initiated SSO, trace utility"
  - "trace utility"
ms.assetid: a53444d1-3f63-42a6-8ee6-b60ff9af9e41
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the Trace Utility in Host Initiated SSO
The primary method of troubleshooting is tracing.  
  
## Tracing  
 Use the Trace command line utility to enable tracing in SSO.  
  
> [!NOTE]
>  For the trace command to function, the file tracelog.exe must be in the following directory:  
>   
>  \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On  
  
> [!NOTE]
>  You can download this file from the following location: [http://go.microsoft.com/fwlink/?LinkId=59534](http://go.microsoft.com/fwlink/?LinkId=59534)  
  
#### To use the trace utility  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **Trace –start –high** to set the tracing level to high and begin the trace.  
  
5.  Run the scenario with host initiated SSO.  
  
6.  Type **Trace –stop** to end the trace. A .bin file is generated in the directory above, which you can send to Microsoft for analysis.  
  
## See Also  
 [Host Initiated SSO](../core/host-initiated-sso.md)