---
title: "Diagnostic tracing and message logging for the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracing"
  - "message logging"
  - "tracing, within the adapter"
  - "tracing, between the adapter client and the adapter"
ms.assetid: 971d34e4-5609-42c6-85b9-d9b1989fc47d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Diagnostic tracing and message logging for the Oracle Database adapter
Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters. This topic provides information about the following two types of tracing supported with [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:  
  
-   WCF tracing between the adapter client and the adapter  
  
-   WCF tracing within the adapter  
  
## WCF Tracing Between the Adapter Client and the Adapter  
 Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter. WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model, and is useful in diagnosing serialization issues. WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client. You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files. Also, you can enable tracing both at design-time and run-time.  
  
- **Tracing at design-time**. For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.  
  
- **Tracing at run-time**. For run-time tracing, you must add the excerpt depending on the application you are using.  
  
  - For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
  - For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.  
  
  To enable WCF tracing, add the following excerpt within the `<configuration>` tag.  
  
```  
<system.diagnostics>  
    <sources>  
      <source name ="System.ServiceModel" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.ServiceModel.MessageLogging"   
              switchValue="Verbose, ActivityTracing">          
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.Runtime.Serialization" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
   </sources>  
   <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"                
           traceOutputOptions="LogicalOperationStack"   
           initializeData="C:\log\WCFTrace.svclog" />  
   </sharedListeners>  
   <trace autoflush="true" />  
  </system.diagnostics>  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="false"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="false"/>  
    </diagnostics>      
  </system.serviceModel>  
```  
  
 This saves the WCF traces to C:\log\WCFTrace.svclog. [WCF Tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more good information.
  
> [!IMPORTANT]
>  Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing. For recommendations, see [Best practices to secure the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)
  
## WCF tracing within the adapter  
 The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages. Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter. You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files. Also, you can enable tracing both at design-time and run-time.  
  
- **Tracing at design-time**. For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.  
  
- **Tracing at run-time**. For run-time tracing, you must add the excerpt depending on the application you are using.  
  
  - For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
  - For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.  
  
  To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag:  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name=" Microsoft.Adapters.OracleDB" switchValue="Information">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"   
   traceOutputOptions="LogicalOperationStack"   
          initializeData="C:\log\AdapterTrace.svclog" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 This saves the WCF traces to C:\log\AdapterTrace.svclog.  
  
## Viewing the traces  
 You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces. See [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).
  
## Configuring Tracking for BizTalk Applications  
 The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports. The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations. [Managing Artifacts](../../core/managing-artifacts.md) includes more info. 

  
## See Also  
[Troubleshoot the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)