---
title: "Trace an adapter with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a4f4758-3e3e-48c4-b4cf-414c2b05d539
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Trace an adapter with the WCF LOB Adapter SDK
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] tracing is built on top of Systems.Diagnostics. You use Microsoft.ServiceModel.Channels trace source for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime.  You use Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse trace source for [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. WCF traces are written to the source named System.ServiceModel.  
  
 The adapter developer can provide a trace source name for the adapter using Microsoft.ServiceModel.Channels.Common.AdapterTrace class. The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] generates a trace wrapper class that can be used by the adapter developer to provide instrumentation in the adapter code.  
  
 For information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).
  
 For information about analyzing traces in WCF, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](https://msdn.microsoft.com/library/ms732023.aspx). 
  
## Sample Trace Wrapper Utility Class  
  
```  
public class EchoAdapterUtilities  
{  
    static AdapterTrace trace = new AdapterTrace("Microsoft.Adapters.Samples.Echo.EchoAdapter");  
  
    /// <summary>  
    /// Gets the AdapterTrace  
    /// </summary>  
    public static AdapterTrace Trace  
    {  
        get  
        {  
            return trace;  
        }  
    }  
}  
```  
  
 The previous utility class can then be used by the adapter developer throughout the adapter code to provide instrumentation data for the adapter consumers.  
  
 EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Connection successfully opened!");  
  
## Enable Tracing for the Adapter and WCF LOB Adapter SDK Runtime  
 You can enable tracing provided in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] by adding the following section in the app.config file of the application using the adapter.  
  
```  
\<system.diagnostics>  
  <sources>  
    <source name="Microsoft.Adapters.Samples.Echo.EchoAdapter" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
    <source name="Microsoft.ServiceModel.Channels" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\TestEchoAdapter_Browse.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" />  
\</system.diagnostics>  
```  
  
 You can use the add element to specify the name and type of the trace listener you want to use. In our example configuration, we named the Listener "xmlTrace" and added the standard .NET Framework trace listener (System.Diagnostics.XmlWriterTraceListener) as the type we want to use. You can add any number of trace listeners for each source. For example, in the following examples, we also added another listener named "textTrace" that uses the .NET Framework trace listener System.Diagnostics.TextWriterTraceListener. If the trace listener emits the trace to a file, you must specify the output file location and name in the configuration file. This is done by setting initializeData to the name of the file for that listener.  
  
## Enabling Tracing for the Add Adapter Service Reference Plug-in  
 You can enable tracing for this plug-in by adding the following section in the devenv.exe.config file located in `\Program Files (x86)\Microsoft Visual Studio\Common7\IDE`.
  
```  
\<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
\</system.diagnostics>  
```  
  
## Enable Tracing for the Consume Adapter Service Add-in  
 You can enable tracing for this add-in by adding the following section in the BTSNTSVC.exe.config file located in `\Program Files (x86)\Microsoft BizTalk Server`.  
  
```  
\<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
\</system.diagnostics>  
```  
  
## See Also  
 [Troubleshoot adapter created using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)