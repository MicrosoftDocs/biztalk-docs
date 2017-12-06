---
title: "Mainframe Printing1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94ca44be-4103-4b97-b5ef-1b83ca408a3b
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Mainframe Printing

##LU1 and LU3 data streams
Mainframe printing supports both LU 1 and LU 3 data streams. It also includes pass-through support from the host for Intelligent Printer Data Stream (IPDS). Using IPDS, mainframe print jobs can be printed on LAN printers without changing either the print job or the host application.  

Connections between mainframe printing and local printer:  
 ![](../core/media/prn01.gif)  
  
Host Print service provides print emulation for three LU types: LU 3, LU 1, and LU 6.2 (APPC). The LU type defines the characteristic of the host data stream. LU 3 and LU 1 printing use a 3270 data stream over a session to a mainframe. APPC printing uses a LU 6.2 data stream over a session to an IBM AS/400. The following sections provide an overview of LU 3 and LU 1 printing. APPC printing is discussed under the AS/400 section later in this section.  
  
The Host Print service must run in a user account that has permission to access the defined network printer (or printers). For example, if you are printing to a printer attached to a Windows server computer, the Host Print service must run in an account that is recognized by Windows Active Directory.  
  
## See Also  
 [Host Print Service (Operations)](../core/host-print-service-operations.md)