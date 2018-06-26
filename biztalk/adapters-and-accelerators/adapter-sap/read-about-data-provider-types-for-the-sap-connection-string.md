---
title: "Read about Data Provider types for the SAP Connection String | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Data Provider for SAP, connection string"
  - "ADO, connection string"
ms.assetid: 7a46eaae-604f-4bae-924b-9f6d43a6e8a0
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Read about Data Provider types for the SAP Connection String
To establish connectivity to an SAP system, ADO.NET clients must specify the SAP connection properties in the form of a connection string. The format for the SAP ADO connection string looks like:  

```  
[Property1]=[Value1];[Property2]=[Value2];....  
```  

 The connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] can have the following types:  

- **TYPE A:** An application host–based connection in which the connection URI specifies an application server through which the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] connects to the SAP system.  

- **TYPE B:** A load-balanced connection in which the connection URI specifies a message server through which the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] connects to the SAP system.  

- **TYPE D:** A destination-based connection in which the connection URI specifies a destination in the saprfc.ini file that contains the connection parameters for the SAP system.  

  The following table describes how these connections are specified in the connection URI.  

|TYPE|Property 1|Property 2|Description|  
|----------|----------------|----------------|-----------------|  
|A|ASHOST (Application Server Host)|SYSNR (SAP System Number)|Specifies an application host-based connection.|  
|B|MSHOST (Message Server Host)|R3NAME (SAP R3 Name)|Specifies a load balancing connection through a message server. For a load balancing connection, an optional server group can be specified.|  
|D|DEST (Destination that contains the connection parameters in the saprfc.ini file)|-|Specifies a destination-based connection. The SAP connection parameters are contained in the specified destination in the saprfc.ini file. Only TYPE A and TYPE B connections can be specified in the destination. **Note:**  If you specify connection values in the saprfc.ini file, make sure the file is located in the same folder as the .exe that accesses the file or at a standard location as required by the SAP system. For more information, see the SAP documentation.|  

 Based on the type of connection, the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] can contain the following properties.  


|               Property                | Used for TYPE |                                                                                                                                                                                                                                               Description                                                                                                                                                                                                                                                |
|---------------------------------------|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Application Server Host (ASHOST)    |       A       |                                                                                                                                                                                                                                 Name of the SAP application server host.                                                                                                                                                                                                                                 |
|         System Number (SYSNR)         |       A       |                                                                                                                                                                                                                                          The SAP system number                                                                                                                                                                                                                                           |
| Application Server Group Name (GROUP) |       B       |                                                                                                                                                                                              Name of the SAP server group. This is an optional group of application servers in a load balancing connection.                                                                                                                                                                                              |
|     Message Server Host (MSHOST)      |       B       |                                                                                                                                                                                                                                   Name of the SAP message server host                                                                                                                                                                                                                                    |
|    Message Server Service (MSSERV)    |       B       | Name of the SAP message server service as specified in the \<system drive\>:\WINDOWS\system32\drivers\etc\services file. If you do not specify a value, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] assumes this to be "sapms\<R/3 system name\>". For example, if the R/3 system name is DV1, the adapter assumes the message server service name to be "sapmsDV1".<br /><br /> However, if the entry in the services file is different, you must specify that value. |
|       R/3 System Name (R3NAME)        |       B       |                                                                                                                                                                                                                                            The SAP R/3 name.                                                                                                                                                                                                                                             |
|          Destination (DEST)           |       D       |                                                                                                                                                                                                                        Picks the connection parameters from the saprfc.ini file.                                                                                                                                                                                                                         |
|            Client (CLIENT)            |     A,B,D     |                                                                                                                                                                                                                                          The SAP client number                                                                                                                                                                                                                                           |
|            Language (Lang)            |     A,B,D     |                                                                                                                                                                                                                                                 Language                                                                                                                                                                                                                                                 |
|           Password (PASSWD)           |     A,B,D     |                                                                                                                                                                                                                                          The SAP user password                                                                                                                                                                                                                                           |
|            Username (USER)            |     A,B,D     |                                                                                                                                                                                                                                The user name to connect to an SAP system                                                                                                                                                                                                                                 |
| Enable SAP GUI debugging (AbapDebug)  |     A,B,D     |                                                                                      Optional parameter that specifies whether ABAP debugging from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] is enabled and whether the adapter uses the SAP GUI for debugging. The value can be True or False; if True, ABAP debugging is enabled and the SAP GUI is opened. The default is False.                                                                                      |
|      Trace RFC SDK(RfcSdkTrace)       |     A,B,D     |                                                                                                                                                                 Optional parameter that specifies whether RFC library tracing is enabled. The value can be True or False; if True, RFC Library tracing is enabled. The default is False.                                                                                                                                                                 |

> [!NOTE]
>  The values provided within parentheses in the Property column are the name of the connection properties that must be specified while providing the connection URI through a programming solution. However, if you are using the DDEX plug-in or SQL Server Import and Export wizard to use the ADO interface, the connection properties are listed as friendly names.  

## Example Connection String for TYPE A  
 An example connection string for TYPE A would look like:  

```  
TYPE=A; ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  

> [!NOTE]
>  By default the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] always considers the connection string to be of TYPE A.  

## Example Connection String for TYPE B  
 An example connection string for TYPE B would look like:  

```  
TYPE=B; R3NAME=NAME1; GROUP=ADAPTER; MSHOST=MSSERVER; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  

## Example Connection String for TYPE D  
 An example connection string for TYPE D would look like:  

```  
TYPE=D; DEST=TESTSAPSRV; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  

 A sample saprfc.ini file resembles:  

```  
DEST=TESTSAPSRV  
TYPE=A  
ASHOST=ADAPSAP47  
SYSNR=00  
```  

 For more information about the saprfc.ini file, see [http://go.microsoft.com/fwlink/?LinkId=91457](http://go.microsoft.com/fwlink/?LinkId=91457).  

 The password for all three connection types must not contain double quotation marks. However, if the password contains any other special characters, the password must be enclosed within double quotation marks. For example:  

```  
ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=",@/:;_ \\";  
```  

> [!IMPORTANT]
>  You must specify the connection parameters for only one connection TYPE A, B, or D. For example, if you specify the Application Server Host in the connection string, you must not specify a Message Server Host name or the R3NAME.  

## See Also  
 [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)