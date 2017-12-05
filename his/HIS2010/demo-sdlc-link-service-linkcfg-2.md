---
title: "Demo SDLC Link Service (Linkcfg )2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 90e1c6c1-e096-4eab-9c3f-8c316086dc6c
caps.latest.revision: 3
---
# Demo SDLC Link Service (Linkcfg )
Linkcfg options for the Demo SDLC link service. You can install the 3270 Continuous Demo, the 3270 File Transfer Demo, the 3270 Logon Demo, the AS400 Demo, and the LU1 and LU3 Printing Demos. Each of these demos is a script file that is run to demonstrate access to mainframe and AS/400 computers.  
  
> [!NOTE]
>  Configuration settings specified with LINKCFG correspond to local link configuration settings in the SNA Manager.  
  
## Syntax  
  
```  
LINKCFG LINKSVC "title" (The quotes must be included.)  
     /SERVER:servername  
     /LSTYPE:"DEMO SDLC Link Service"  
     /SCRIPTFILE: {"3270 Continuous Demo.dem"   |  
                  "3270 File Transfer Demo.dem" |  
                  "3270 Logon Demo.dem"         |  
                  "AS400 Demo.dem"              |  
                  "LU1 Printing Demo.dem"       |  
                  "LU3 Printing Demo.dem"}  
     /DISTRIBUTABLE:  
```  
  
 **/LINKSVC**" *title*" (The quotes must be included.)  
 Enter the name of the service title. The quotes must be included. While any title name can be used, it is recommended that one of the following titles be used:  
  
 **/LSTYPE:**"Demo SDLC Link Service"  
 This parameter is used to list the available options for the Demo SDLC link service. You must type in the exact string as shown above for it to work correctly. The quotes must be included.  
  
 **/SERVER:** *servername*  
 This is the name of the computer on which the link service is to be installed.  
  
 **/SCRIPTFILE:**" *script file*"  
 This is the name of the demonstration script. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] provides the following scripts:  
  
-   `"Continuous Demo.dem"` - this is the 3270 continuous demo script..  
  
-   `"File Transfer Demo.dem"` - this is the file transfer demo script.  
  
-   `"3270 Logon Demo.dem"` - this is the 3270 logon demo script.  
  
-   `"AS400 Demo.dem"` - this is the 5250 demo script.  
  
-   `"LU1 Printing Demo.dem` "- this is the demo script showing LU1 printing.  
  
-   `"LU3 Printing Demo.dem"` - this is the demo script showing LU3 printing. (The quotes must be included.)  
  
## See Also  
 [Linkcfg Reference](../HIS2010/linkcfg-reference1.md)