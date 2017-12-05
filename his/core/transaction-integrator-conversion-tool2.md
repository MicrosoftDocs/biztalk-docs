---
title: "Transaction Integrator Conversion Tool2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01051a53-7ef8-4434-b84e-375d90536df0
caps.latest.revision: 3
---
# Transaction Integrator Conversion Tool
The TIConversionTool command-line utility makes it quick and easy to migrate to Host Integration Server (HIS) 2010 from HIS 2009, HIS 2008, HIS 2006 and HIS 2004. You can use it to convert Window Initiated (WIP) or Host Initiated (HIP) TLBs and .NET assemblies created in earlier versions of HIS to HIS 2010 .NET assemblies. You can use it to convert a single TLB or assembly, or multiple TLBs or assemblies.  
  
 The TIConversionTool.exe is located in the following folders:  
  
|OS|Location|  
|--------|--------------|  
|x64|C:\Program Files\Microsoft Host Integration Server 2010\SysWOW64\|  
|x86|C:\Program Files\Microsoft Host Integration Server 2010\system\|  
  
 You can run the conversion utility from the command line, or call it from another program such a PowerShell. For usage instructions at run time, run TIConversionTool.exe from the command line with no arguments.  
  
 **TIConversionTool Considerations**  
  
-   The TIConversionTool.exe does not migrate the context interface to the new context interface introduced in HIS2010.  
  
-   TheTIConversionTool.exe will update the RE class only when the current RE class is no longer supported.  
  
-   The utility updates old type libraries and .NET assemblies to work with Host Integration Server 2010. Once converted, we recommend that HIS 2006 and 2004 conversions be associated with new matching RE types.  You can associate HIS 2009 conversions with existing HIS 2009 REs, or with new matching HIS 2010 REs.  
  
-   When converting an old type library to a .NET assembly, TI converts Visual Basic version 6.0 Automation data types to Visual Basic .NET types as described in the following table.  
  
    |Visual Basic v6|Visual Basic .NET|  
    |---------------------|-----------------------|  
    |Integer|Short|  
    |Long|Integer|  
    |Currency|Decimal|  
    |Recordset|DataTable|  
    |UDT|Structure|  
  
-   The **NewRecordset** function is not supported in .NET. You must modify code in client applications that use the **NewRecordset** function to create disconnected recordsets.  
  
-   You must recompile existing COM Clients that use declarative binding due to GUID changes.  
  
-   You must use the Import feature in Designer to convert the TLB or .NET assembly in the following cases:  
  
    -   You are converting the old Client Context model to the new Client Context object model.  
  
    -   Your application uses persistence connections.  
  
    -   You want to use features that rely on the new model, such as dynamic REs.  
  
    -   The ProgID of the TLB is greater than 30 characters.  
  
 For more information, see [Working with TI Designer](../core/working-with-ti-designer2.md).  
  
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