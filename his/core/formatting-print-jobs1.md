---
title: "Formatting Print Jobs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9fd4234a-92f0-455f-9fe8-0e53a9e33288
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Formatting Print Jobs
Host Print service can format print jobs by either using the Windows printer driver or by using a Printer Definition Table.  
  
 By default, print jobs submitted by Host Print service to a Windows print queue rely on the Windows printer driver to format the print data and send to the physical printer. Formatting the print data is done by the Windows Graphical Device Interface (GDI).  
  
 In addition to the Windows GDI, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Host Print service supports the use of a Printer Definition Table (PDT), which bypasses the formatting function of the Windows Server printer driver. The PDT file provides a function similar to a printer driver, in that it translates Graphic Device Interface (GDI) calls to control codes specific for a printer.  
  
 Selecting PDT causes the Windows Server Host Print service to treat all received data as transparent. All data is passed directly to the printer, except SCS codes, which are treated differently. Using a PDT, the SCS codes will be translated using the PDT before they are passed to the printer. For more information about Printer Definition Files, see [Printer Definition Files](../core/printer-definition-files2.md).  
  
 The PDT is created in two steps.  
  
1. A source text file is created and called the Printer Definition File (PDF) that defines the codes that can be used to control the printer.  
  
2. A program is used to compile the information in the PDF into a binary file, the PDT that is used by Host Print service.  
  
   For example, if the host sends a byte indicating a new line ('0x15'), the PDT could be used to convert this to a carriage return, line feed ('0x0D0A').  
  
   For more information about creating a PDT, see [Printer Definition Files](../core/printer-definition-files2.md).  
  
### To enable GDI  
  
1.  In SNA Manager, expand the server, and then click **Print Service**.  
  
2.  Right-click a print service displayed in the details pane, and then click **Properties**.  
  
3.  Click the **Job Format** tab, and then select **GDI**.  
  
### To select a PDT for printing  
  
1.  In SNA Manager, expand the server, and then click **Print Service**.  
  
2.  Right-click a print service displayed in the details pane, and then click **Properties**.  
  
3.  Click the **Job Format** tab, select **PDT**, and then click **PDT File**. The **Select Compiled Printer Definition File** dialog box appears.  
  
4.  Select the PDT that you want to use, and then click **Open**.  
  
5.  Click **OK**.  
  
## See Also  
 [Transparency](../core/transparency2.md)