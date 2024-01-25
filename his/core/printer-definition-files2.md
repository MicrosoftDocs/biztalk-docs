---
description: "Learn more about: Printer Definition Files"
title: "Printer Definition Files2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Printer Definition Files
Host Print service enables you to specify the capabilities of a printer to override the defaults provided by the Windows printer driver.  
  
 By default, jobs submitted by Host Print service to a Windows print queue rely on the printer's Windows driver to send to the physical printer the data required to perform such formatting tasks as breaking lines and starting a new page.  
  
 Applications that bypass the formatting function of the Windows printer driver can use codes specified in a printer definition file to control the physical printer for a particular printer session under Host Print service. To use the file, open the properties page of the printer session, click the **Printing** tab, select **PDT**, and then type the fully qualified path of the file in the box. For more information about using the PDT file, click **Help** on the printer session properties dialog box.  
  
 Creating a printer definition file consists of two steps: First, you create a source text file that defines the codes that can be used to control the printer. Second, you run a program to compile the information in the text file into a binary file that can be used by Host Print service.  
  
## In This Section  
 [Creating the Source Text File](../core/creating-the-source-text-file1.md)
