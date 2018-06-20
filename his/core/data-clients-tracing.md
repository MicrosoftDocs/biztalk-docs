---
title: "Data Clients Tracing | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54c04404-7c81-4c86-94b4-b7ef844cca85
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Clients Tracing
There are multiple options for tracing, which can help to capture problems in the consumer, service components, provider, networking and host data source.  
  
## SQL consumer tracing using SQL Server Profiler  
 SQL Server Profiler is a graphical user interface to SQL Trace for monitoring an instance of the Database Engine or Analysis Services. You can capture and save data about each event to a file or table to analyze later. For more information, see [Introducing SQL Server Profiler](http://go.microsoft.com/fwlink/?LinkID=180433) (http://go.microsoft.com/fwlink/?LinkID=180433).  
  
## Data provider tracing using Provider Trace Utility  
 The HIS Trace Utility captures and saves information from the Microsoft DB2 and Informix network client connections, provider interfaces and data messages. For more information, see Trace Utility Help and SNA Trace Utility.  
  
## Network tracing using Network Monitor  
 The Network Monitor captures network traffic for display and analysis. It enables you to perform tasks such as analyzing previously captured data in user-defined methods, extracting data from defined protocol parsers. It includes a Distributed Data Management (DDM) parser for use with the HIS data network clients. Contact Microsoft Customer Support Services for a copy of the DDM parser. For more information, see [Network Monitor](http://go.microsoft.com/fwlink/?LinkID=180448) (http://go.microsoft.com/fwlink/?LinkID=180448).  
  
## DB2 server tracing using IBM tools  
 For more information, see the IBM DB2 Administration Guide for the applicable DB2 platform and version.  
  
## Informix server tracing using IBM tools  
 For more information, see the IBM Informix Administration Guide for the applicable Informix platform and version.  
  
## Windows Server events using Event Viewer  
 The Event Viewer is a Microsoft Management Console (MMC) snap-in that enables you to browse and manage event logs. For more information, see [Event Viewer](http://go.microsoft.com/fwlink/?LinkID=131274) (http://go.microsoft.com/fwlink/?LinkID=131274).  
  
## Host File Client and Data Provider Tracing  
 Host File Client and ADO.NET Data Provider for Host Files (Host File Client) supports a Microsoft Host Integration Text Trace Listener that is configured using a HIDT (Host Integration Tracing Definition) configuration file that is referenced in the system diagnostics element of the data consumer app.config file.  
  
### Data Consumer App.Config File  
 The data consumer app.config file contains a Microsoft Host Integration Tracing configuration section element and a Host Integration Server Text File Listener element that control the Host File Client tracing.  In this example, the MsHostFileClient.HITD (Host Integration Tracing Definition) file should be in the Data Consumer program directory.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <configSections>  
    <section name="microsoft.hostintegration.tracing" type="Microsoft.HostIntegration.Tracing.TraceSection, Microsoft.HostIntegration.Tracing.Configuration, Culture=neutral, Version=9.0.1000.0, PublicKeyToken=31bf3856ad364e35" />  
  </configSections>  
  
  <microsoft.hostintegration.tracing   
    traceDefinitionFile=" MsHostFileClient.HITD" />  
  
  <system.diagnostics>  
    <trace>  
      <listeners>  
        <add  
          name="HisTextFileListener"  
          type="Microsoft.HostIntegration.Tracing.HisTextFileTraceListener, Microsoft.HostIntegration.Tracing.Runtime, Culture=neutral, Version=9.0.1000.0, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"  
          maxTraceEntries="1000000"  
          traceFileFolder="C:\Program Files\Microsoft Host Integration Server 2013\traces\"  
          autoFlush="true"  
          fileNamePreamble="MsHostFileClient"  
          allowNonHisTracingToCreateFile="true"   
    />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
  <startup>   
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
    </startup>  
</configuration>  
```  
  
#### Configuration Section  
 The **configSections** element contains configuration section and namespace declarations for the Microsoft Host Integration Tracing component.  
  
 **Configuration Section Name**  
  
 The section **name** attribute defines the name of the Microsoft Host Integration Tracing component. This **required** attribute is accepts a **string**, with a value of **Microsoft.hostintegration.tracing**.  
  
 **Configuration Section Type**  
  
 The **type** attribute defines the type of the Microsoft Host Integration Tracing text trace listener. This **required** attribute is accepts a string, with a value of **Microsoft.HostIntegration.Tracing.TraceSection, Microsoft.HostIntegration.Tracing.Configuration, Culture=neutral, Version=7.0.2300.0, PublicKeyToken=31bf3856ad364e35**.  
  
#### Host Integration Tracing Section  
 The **microsoft.hostintegration.tracing** element contains configuration information for the Microsoft Host Integration Tracing component text trace listener.  
  
 **Trace Definition File**  
  
 The **traceDefinitionFile** attribute defines the name of the Microsoft Host Integration Tracing text trace listener output file. This **required** attribute is accepts a **string**, with a value representing a trace output path and file name.  
  
> [!NOTE]
>  Each user account must have write access to the traces folder, in order to insert lines into the text trace file. Each user account requires the Folder Access Control List settings associated with the HIS Runtime Users Local Group. See section titled Security and Protection for more information.  
  
### System Diagnostics  
 The **system.diagnostics** element contains additional configuration for the Microsoft Host Integration Tracing component Text Trace Listener.  
  
 **Trace Listener Name**  
  
 The **name** attribute defines the name of the Host File Client text trace listener. This **required** attribute is accepts a **string**, with a value of **HisTextFileListener**.  
  
 **Trace Listener Type**  
  
 The **type** attribute defines the type of the DRDA Service text trace listener. This **required** attribute accepts a **string**, with a value of **Microsoft.HostIntegration.Tracing.HisTextFileTraceListener, Microsoft.HostIntegration.Tracing.Runtime, Culture=neutral, Version=7.0.2300.0, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL**.  
  
 **Maximum Trace Entries**  
  
 The **maxTraceEntries** attribute instructs the Host File Client to trace up to a maximum number of entries, and then to stop tracing. This **optional** attribute accepts an **integer**. The default value is **1000000**.  
  
 **Trace File Folder**  
  
 The **traceFileFolder** attribute instructs the Host File Client text trace listener where to write the text listener trace output file. This **optional** attribute accepts a **string** value. The default value is **C:\Program Files\Microsoft Host Integration Server 2013\traces**.  
  
> [!NOTE]
>  Each user account must have write access to the traces folder, in order to insert lines into the text trace file. Each user account requires the Folder Access Control List settings associated with the HIS Runtime Users Local Group. See section titled Security and Protection for more information.  
  
 **Automatic Flush**  
  
 The **autoFlush** attribute instructs the DRDA Service to flush data automatically to the trace listener. This optional attribute accepts a **Boolean** value. The default is **false**.  
  
> [!NOTE]
>  The Host File Client text trace listener can flush trace data automatically to the trace listeners, which ensures the trace data is captured but will increase disk I/O and reduce overall system performance. To improve performance, set autoFlush=false, to disable automatic trace flush.  
  
 **Trace File Name**  
  
 The **name** attribute defines the name of the Host File Client text trace output file. This **required** attribute is accepts a **string**.  
  
 **Trace Listener Initialization**  
  
 The **allowNonHisTracingToCreateFile** attribute defines whether trace can be initiated by a component other than the Host File Client and Microsoft Host Integration Tracing. This **required** attribute is accepts a **Boolean**, with a default value of **false**.  
  
### Host Integration Tracing Definition (HITD) File  
 The Host Integration Tracing Definition (HIDT) configuration file defines the trace level for the Host Integration Server Text File Listener.  
  
#### Trace Containers  
 The **containers** element includes container elements defining trace levels for each trace point.  
  
 **Trace Container Name**  
  
 The **name** attribute defines the name of the trace container. This **required** attribute is accepts a **string**, with a value of **HostFiles**.  
  
 **Trace Point Name**  
  
 The **name** attribute defines the name of the trace source point. This **required** attribute is accepts a **string**. The **default** value is an **empty string**.  
  
|||  
|-|-|  
|**Value**|**Description**|  
|HostFiles|ADO.NET Provider for Host Files|  
|Transport|Host File Client for DDM RLIO|  
|Aggregate Converter|Host Integration Server Encoder Aggregate Converter|  
|Primitive Converter|Host Integration Server Encoder Primitive Converter|  
  
 <em>**Table 1.</em>* Host File trace source point names.*  
  
 **Trace Level**  
  
 The **traceLevel** attribute instructs the Host File Client to trace defined collections of information, from a minimum to a maximum level of tracing. This **optional** attribute accepts a **string** value. The **default** value is an **empty string**.  
  
|||  
|-|-|  
|**Value**|**Description**|  
|Fatal|Output fatal messages.|  
|Error|Output error messages.|  
|Warning|Output warning messages, error messages, and fatal messages.|  
|Information|Output information messages, warning messages, error messages, and fatal messages.|  
|Verbose|Output all messages.|  
|Data|Output all messages, and user data.|  
|Debug|Output all messages, user data, and debug data.|  
  
 <em>**Table 2.</em>* Host File text trace listener levels.*  
  
```  
<containers>  
  <container name="HostFiles">  
    <tracePoint name="MsHostFileClient">  
      <traceLevel level="All">  
      </traceLevel>  
    </tracePoint>  
    <tracePoint name="Transport">  
      <traceLevel level="All">  
      </traceLevel>  
    </tracePoint>  
    <tracePoint name="Aggregate Converter">  
      <traceLevel level="All">  
      </traceLevel>  
    </tracePoint>  
    <tracePoint name="Primitive Converter">  
      <traceLevel level="All">  
      </traceLevel>  
    </tracePoint>  
  </container>  
</containers>  
```  
  
## See Also  
 [Data Integration (Troubleshooting)](../core/data-integration-troubleshooting-2.md)