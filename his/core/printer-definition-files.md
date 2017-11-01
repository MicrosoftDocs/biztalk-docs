---
title: "Printer Definition Files2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b89e01fc-ba4d-4f85-95ed-f5284055bb0c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Printer Definition Files
Host Print service enables you to specify the capabilities of a printer to override the defaults provided by the Windows printer driver.  
  
 By default, jobs submitted by Host Print service to a Windows print queue rely on the printer's Windows driver to send to the physical printer the data required to perform such formatting tasks as breaking lines and starting a new page.  
  
 Applications that bypass the formatting function of the Windows printer driver can use codes specified in a printer definition file to control the physical printer for a particular printer session under Host Print service. To use the file, open the properties page of the printer session, click the **Printing** tab, select **PDT**, and then type the fully qualified path of the file in the box. For more information about using the PDT file, click **Help** on the printer session properties dialog box.  
  
 Creating a printer definition file consists of two steps: First, you create a source text file that defines the codes that can be used to control the printer. Second, you run a program to compile the information in the text file into a binary file that can be used by Host Print service.  
  
## In This Section  
 [Creating the Source Text File](../core/creating-the-source-text-file.md)