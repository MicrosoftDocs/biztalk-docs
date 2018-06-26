---
title: "Diagnostic Tracing and Message Logging in the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6599b4d-5650-4592-96af-ee43fb36357d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Diagnostic Tracing and Message Logging in the SQL adapter
Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters. Adapter clients can activate diagnostic tracing at two levels:  
  
- Between the adapter client and the adapter  
  
- Within the adapter  
  
  This section provides information about activating tracing at these levels.  
  
## Tracing Between the Adapter Client and the Adapter  
 Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter. WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model and is useful in diagnosing serialization issues. WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client. You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files. Also, you can enable tracing both at design time and run time.  
  
- **Tracing at design time**. For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.  
  
- **Tracing at run time**. For run-time tracing, you must add the excerpt depending on the application you are using.  
  
  - For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
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
  
 This saves the WCF traces to C:\log\WCFTrace.svclog. For more information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).  
  
> [!IMPORTANT]
>  Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing. For recommendations see [Best practices to secure the SQL adapter](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md).
  
## Tracing Within the Adapter  
 The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages. Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter. You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files. Also, you can enable tracing both at design time and run time.  
  
- **Tracing at design time**. For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.  
  
- **Tracing at run time**. For run-time tracing, you must add the excerpt depending on the application you are using.  
  
  - For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
  - For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.  
  
  To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag.  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Sql" switchValue="Information">  
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
  
## Viewing the Traces  
 You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces. For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubles](https://msdn.microsoft.com/library/aa751795.aspx).
  
## Configuring Tracking for BizTalk Applications  
 The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports. The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations. For more information about configuring tracking for BizTalk applications, see the [Managing Artifacts](../../core/managing-artifacts.md).
  
 You can also use Health and Activity Tracking (HAT) to view historical or tracked data. For more information, see [Viewing Historical and Tracked Data](../../core/viewing-historical-and-tracked-data.md).
  
## See Also  
 [Troubleshoot the SQL adapter](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)