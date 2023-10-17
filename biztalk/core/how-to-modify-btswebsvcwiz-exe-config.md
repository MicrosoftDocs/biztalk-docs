---
description: "Learn more about: How to Modify BTSWebSvcWiz.exe.config"
title: "How to Modify BTSWebSvcWiz.exe.config"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Modify BTSWebSvcWiz.exe.config
You can enable tracing to debug the BizTalk Web Services Publishing Wizard by uncommenting the \<add\> node in the BTSWebSvcWiz.exe.config file. If the trace listener node is uncommented and the *initializeData* parameter is unchanged, BizTalk Server writes the trace file output to the current directory. Alternatively, you can set the trace level of **ApplicationTraceSwitch** and set the path name of the trace file.

 BTSWebSvcWiz.exe.config is located in the same directory as the BTSWebSvcWiz.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].

 The following is an example of an uncommented \<add\> node in BTSWebSvcWiz.exe.config file:

```
<system.diagnostics>
  <switches>
    <!-- TraceLevel 0=Off, 1=Error, 2=Warning, 3=Info, 4=Verbose -->
    <add name="ApplicationTraceSwitch" value="4" />
  </switches>
  <trace autoflush="true" indentsize="4">
    <listeners>
      <!--add name="Trace"
       type="System.Diagnostics.TextWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
       initializeData="BTSWebSvcWiz.trace.log" /-->
    </listeners>
  </trace>
</system.diagnostics>
```

 This tracing feature uses the Trace class in the .NET Framework. For more information about the Trace class, see the Microsoft MSDN Web site at [https://go.microsoft.com/fwlink/?LinkId=67886](/dotnet/api/system.diagnostics.trace).

 For information about **TextWriterTraceListener**, see "TextWriterTraceListener" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [https://go.microsoft.com/fwlink/?LinkId=62267](/dotnet/api/system.diagnostics.textwritertracelistener).

## See Also
 [Debugging Published Web Services](../core/debugging-published-web-services.md)