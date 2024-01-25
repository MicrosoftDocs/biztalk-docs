---
description: "Learn more about: Enabling System.Net Logging"
title: "Enabling System.Net Logging"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Enabling System.Net Logging
You can enable logging for the `System.Net` and `System.Net.Sockets`[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] namespace for the BTSNtSvc.exe service. This will cause a detailed log file to be created containing information that may help you identify issues with your BizTalk Server installation.

> [!NOTE]
>  This is a feature of the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] and will work in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] or later.

 Tracing is enabled by modifying the application configuration file for **BTSNtSvc.exe**,  **BTSNtSvc.exe.config**. It can be found in the BizTalk Server installation path; if you installed BizTalk Server to the default location, BtsNtSvc.exe will be in the directory [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].

 To modify **BTSNtSvc.exe.config**, open the configuration file and paste the code below into the `<configuration>` element using Notepad or your favorite text editor.

```
<system.diagnostics>
  <sources>
    <source name="System.Net" switchValue="Verbose">
      <listeners>
        <add name="System.Net"/>
      </listeners>
    </source>
    <source name="System.Net.Sockets" switchValue="Verbose">
      <listeners>
        <add name="System.Net"/>
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="System.Net"
          type="System.Diagnostics.TextWriterTraceListener"
          initializeData="System.Net..log"/>
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

 The log file will be written to the same directory that contains BTSNtSvc.exe. If you installed to the default location, it will be written to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].

## See Also
 [Interpreting Network Tracing](/dotnet/framework/network-programming/interpreting-network-tracing)
