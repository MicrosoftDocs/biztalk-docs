---
title: "Compiling the Source Text File2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fd0dfb-6478-473c-bc41-3883f033688c
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Compiling the Source Text File
After you have created the source text file, the next step is to compile the file using the Pdfcomp (PDFCOMP.EXE) utility located in the \\*platform*\SYSTEM\PRINTSRV directory. To run Pdfcomp, type the following at the command prompt.  
  
```  
input_file output_file  
  
```  
  
 You must specify the full name (including file extensions) of the input and output files.  
  
 For example, to compile the sample PDF file, copy PDFCOMP.EXE and HPLJ2.PDF to a directory on the server's hard disk, open a Command Prompt window and change the current directory to the directory containing the copied files. Then, type the following at the command prompt.  
  
```  
  
hplj2.pdf hplj2.pdt  
  
```  
  
 This creates the binary PDT file in the current directory. Specifying this file in the properties of a printer session allows Host Print service to send preformatted data to the printer, bypassing the formatting function of the Windows printer driver.  
  
 Compilation of the PDF file into a PDT is not strictly necessary. If an uncompiled PDF file is selected in a Print Session under the SNA Manager, the compilation is performed automatically each time the print session is used. This feature has a performance overhead and is available mainly for ease of development. For production systems, it is strongly recommended that you pre-compile PDF files.  
  
## See Also  
 [Printer Definition Files](../core/printer-definition-files2.md)