---
title: "Host Print Service (Operations)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cb047f4-f763-495c-b771-fc851c537c81
caps.latest.revision: 4
---
# Host Print Service (Operations)
Host Print service provides server-based 3270 and 5250 print emulation, allowing mainframe and AS/400 applications to print to a LAN printer supported by Windows operating system. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Host Print service enables centralized control of LU print resources. You can administer all Host Print service functions using SNA Manager, including margin control, fonts, and characters per line. Host Print service also supports print-to-file with auto-incrementing file names. You can configure the file naming scheme for each printer LU.  
  
 The following three methods of printing host information are available:  
  
-   **Screen printing.** This method allows any 3270 or 5250 emulator to print what is on the display using print screen features of the client operating system. The printer output can be directed to a printer attached to the client computer or the network.  
  
-   **Client-redirected printing.** This method delivers an SNA host printer data stream (such as 3287) to the appropriate emulation application running on a Host Integration Client computer. The client software converts the data stream into data that can be printed locally or to a network printer.  
  
-   **Server-based redirected printing.** This method uses a server process to convert SNA host printer data streams into data that can be directed to a local or network printer.  
  
## In This Section  
 [Host Print Services](../core/host-print-services2.md)  
  
 [Mainframe Printing](../core/mainframe-printing2.md)  
  
 [Configuring Host Print Service](../core/configuring-host-print-service1.md)  
  
 [AS/400 (APPC) Printing](../core/as-400-appc-printing2.md)  
  
 [Printer Definition Files](../core/printer-definition-files1.md)