---
title: "Diagnostic Tracing and Message Logging for the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracing, between the adapter client and the adapter"
  - "logging, troubleshooting"
  - "troubleshooting, tracing and message logging"
  - "tracing, between the adapter and the LOB application"
  - "message logging, troubleshooting"
  - "tracing, troubleshooting"
ms.assetid: fd2de692-45b7-45bc-b79c-381f3b1cf592
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Diagnostic Tracing and Message Logging for the Siebel adapter
Adapter clients can enable diagnostic tracing to effectively diagnose problems encountered while using the adapters. Adapter clients can activate tracing at three different levels:  
  
- Between the adapter client and the adapter  
  
- Within the adapter  
  
- Between the adapter and the line-of-business (LOB) application  
  
  This section provides information about activating tracing at these levels.  
  
## Tracing between the adapter client and the adapter  
 Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter. WCF tracing is used to trace the input XMLs coming from the adapter client using the WCF service model and is useful in diagnosing serialization issues. WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client. You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files. Also, you can enable tracing both at design-time and run-time.  
  
- **Tracing at design-time**. For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.  
  
- **Tracing at run-time**. For run-time tracing, you must add the excerpt depending on the application you are using.  
  
  - For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
  - For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.  
  
  To enable WCF tracing, you must add the following excerpt within the `<configuration>` tag:
  
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
  
 This saves the WCF traces to C:\log\WCFTrace.svclog. [WCF tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more info.
  
> [!IMPORTANT]
>  Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing. See [Best practices to secure the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md) 
  
## Tracing Within the Adapter  
 The adapters in the BizTalk Adapter Pack log different categories of useful information to the trace file such as errors, warnings, and information. Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter. You can activate [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files. Also, you can enable tracing both at design-time and run-time.  
  
- **Tracing at design-time**. For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.  
  
- **Tracing at run-time**. For run-time tracing, you must add the excerpt depending on the application you are using.  
  
  - For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
  - For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.  
  
  To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, you must add the following excerpt within the `<configuration>` tag:  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Siebel" switchValue="Information">  
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
  
 This would save the WCF traces to C:\log\AdapterTrace.svclog.  
  
## Tracing Between the Adapter and the LOB Application  
 You must enable tracing for communication between the adapter and the LOB application to diagnose issues you suspect within the LOB application. Adapters also depend on LOB tracing (client/server side) to get access to this information. The specifics of turning on LOB tracing are excluded from this document.  
  
 Additionally, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides a binding property (**LogData**), which if set to **True** and if the trace level is set to **Verbose**, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] logs the information flow between the adapter and the Siebel system. This information is logged along with the adapter traces in the same trace file.  
  
 For more information about this binding property, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
## Viewing the Traces  
 You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces. For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).  
  
## Configuring Tracking for BizTalk Applications  
 The BizTalk Administration Console enables you to configure various tracking options for things such as send ports, receive ports. The tracking configuration settings enable you to track inbound/outbound event data, message properties, message bodies, and orchestrations. For more information about configuring tracking for BizTalk applications, see [Managing Artifacts](../../core/managing-artifacts.md).
  
You can also use Group Hub to [Viewing Tracked Message and Instance Data](../../core/viewing-tracked-message-and-instance-data.md), including a tracking checklist, and best practices.
  
## See Also  
[Troubleshoot the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)