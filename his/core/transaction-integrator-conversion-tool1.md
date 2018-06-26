---
title: "Transaction Integrator Conversion Tool1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a2c759d-40d8-407a-ade6-d5c017984214
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Integrator Conversion Tool
The TIConversionTool command-line utility makes it quick and easy to migrate to Host Integration Server from HIS 2010, HIS 2009, HIS 2008, HIS 2006 and HIS 2004. You can use it to convert Window Initiated (WIP) or Host Initiated (HIP) TLBs and .NET assemblies created in earlier versions of HIS to Host Integration Server .NET assemblies. You can use it to convert a single TLB or assembly, or multiple TLBs or assemblies.  

 The TIConversionTool.exe is located in the following folders:  


| OS  |                             Location                              |
|-----|-------------------------------------------------------------------|
| x64 | C:\Program Files\Microsoft Host Integration Server 2013\SysWOW64\ |
| x86 |  C:\Program Files\Microsoft Host Integration Server 2013\system\  |

 You can run the conversion utility from the command line, or call it from another program such a PowerShell. For usage instructions at run time, run TIConversionTool.exe from the command line with no arguments.  

 The TIConversion Tool when ran will produce the following a directory with the same name as the assembly or TLB being converted.  In that directory the following files and a bin directory that contains the converted TI assembly are placed.  

1. xxxx.asmx - configuration file for deploying  TI assembly as web service  

2. xxxx.svc - configuration file for deploying TI assembly as a wcf service  

3. xxxx.xsd - schema file for to be used with BizTalk Host Application Adapter  

4. web.config.WCF - wcf web config file for IIS deployment  

5. web.config.WS - asmx web config file for II deployment  

6. bin/xxxx.dll - Converted TI assembly.  

   **TIConversionTool Considerations**  

- The TIConversionTool.exe migrates the context interface to the new context interface introduced in Host Integration Server.  

- TheTIConversionTool.exe will update the RE class only when the current RE class is no longer supported.  

- The utility updates old type libraries and .NET assemblies to work with Host Integration Server. Once converted, we recommend the conversions be associated with new RE configuration.  You can associate HIS 2009 and HIS 2010 conversions with existing HIS REs, or with new matching Host Integration Server REs.  

- When converting an old type library to a .NET assembly, TI converts Visual Basic version 6.0 Automation data types to Visual Basic .NET types as described in the following table.  


  | Visual Basic v6 | Visual Basic .NET |
  |-----------------|-------------------|
  |     Integer     |       Short       |
  |      Long       |      Integer      |
  |    Currency     |      Decimal      |
  |    Recordset    |     DataTable     |
  |       UDT       |     Structure     |


- The **NewRecordset** function is not supported in .NET. You must modify code in client applications that use the **NewRecordset** function to create disconnected recordsets.  

- You must recompile existing COM Clients that use declarative binding due to GUID changes.  

- You must use the Import feature in Designer to convert the TLB or .NET assembly in the following cases:  

  -   Your application uses persistence connections.  

  -   You want to use features that rely on the new model, such as dynamic REs.  

  -   The ProgID of the TLB is greater than 39 characters.  

- TI TLB's contained two interfaces for TI context when the tlb  was configured to allow the use of clientContext.. HIS2013 TI .Net assemblies contain only a single interface when configured to allow the use of clientContext.  A client application using a tlb with direct call model didn't require the context value defined within the parameter list of the TI method call. In HIS2013 After running the tlb through TIconversiontool.exe the result will be replaced with a .Net assembly.  the customer must include the context value within the parameter list of the TI method call.  

  For more information, see [Working with TI Designer](../core/working-with-ti-designer1.md).  

## Usage  

```  
TIConversionTool [[/f] libraryname1 [libraryname1 ...] [/o outputdir] [/fl fileList1 [fileList2 ...]] [/l logFile]]  
```  

## Syntax  
 **/f**  
 Specify libraries to be converted.  

 **/fl**  
 Specify a text file that contains a list of libraries to be converted.  

 **/o**  
 Specify the directory that will contain the converted assemblies.  

 **/l**  
 Specify the log file name.  

 **/d**  
 Specify a directory that contains the libraries to be converted.  

 **/ds**  
 Specify a directory that contains the libraries to be converted including those in the subdirectories.  

 **/ow**  
 Overwrite all existing assemblies.  

 **/sk**  
 Skip type libraries whose output assemblies exist already.  

 **/ol**  
 Overwrite log file if exists.  

## Sample Usage  

```  
TIConversionTool /f c:\temp\ComClnt1.tlb  

TIConversionTool /f c:\temp\NetClnt1.dll /o c:\output  

TIConversionTool /f c:\temp\NetClnt1.dll NetClnt2.dll  

TIConversionTool /f c:\temp\NetClnt1.dll NetClnt1.dll /o c:\output  

TIConversionTool /fl fileList.txt  

TIConversionTool /fl fileList.txt /l fileList.log  

TIConversionTool /fl fileList.txt /o c:\output  

```  

> [!WARNING]
>  Command-line parameters specified without using the above flags are treated as libraries to be converted.