---
title: "How to Enable Tracing in BAM | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4da99e74-a41d-4ab1-a07d-e3bee6187216
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable Tracing in BAM
You can enable tracing in BAM to help troubleshoot problems within the following five BAM components:  
  
-   BAM Management utility  
  
-   BAM event bus  
  
-   BAM portal  
  
-   BAM alerting  
  
-   BAM WCF Interceptor  
  
## Enabling Tracing for the BAM Management Utility  
 You can obtain information about deployment failures by enabling tracing for the BAM Management utility. You can do this in two ways. You can enable tracing via the command line for specific BM.exe commands, or you can modify the BAM Management utility configuration file to enable tracing for all BM.exe commands.  
  
### Using the Command Line  
 BM.exe command line tracing is activated using the **-Trace:on&#124;off** switch. Using the Trace switch overrides the settings in the configuration file.  
  
 The switch is used in conjunction with any normal BM.exe command.  
  
 For example:  
  
 **bm.exe deploy-all -DefinitionFile:PO.xml –Trace:On**  
  
### Using the Configuration File  
 You can enable tracing by modifying the BM.exe.config configuration file located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking folder. This file contains a **system.diagnostics** section which contains the tracing elements. Remove the comment to enable tracing. By default, tracing is not enabled.  
  
 `<system.diagnostics>`  
  
 `<!-- To turn on BAM tracing, remove this comment or use the "-trace:on" command-line switch`  
  
 `<switches>`  
  
 `<add name="bm" value="1" />`  
  
 `<add name="Microsoft.BizTalk.Bam.Management" value="1" />`  
  
 `</switches>`  
  
 `-->`  
  
## Enabling Tracing for the BAM Event Bus  
 Enabling tracing for the BAM event bus can help you diagnose two classes of database storage errors:  
  
- Storage errors originating from events from the BizTalk Server service when using the Tracking Profile Editor.  
  
- Storage errors generated when using the buffered event stream APIs.  
  
  To enable tracing for the BAM event bus, edit or add the following section of the BTSNTSvc.exe.config file located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] folder.  
  
  `<system.diagnostics>`  
  
  `<switches>`  
  
  `<add name="Microsoft.BizTalk.Bam.EventBus" value="1" />`  
  
  `</switches>`  
  
  `<trace autoflush="true" indentsize="4">`  
  
  `<listeners>`  
  
  `<add name="Text" type="System.Diagnostics.TextWriterTraceListener" initializeData="c:\tdds.log"/>`  
  
  `</listeners>`  
  
  `</trace>`  
  
  `</system.diagnostics>`  
  
#### To enable tracing for the BAM Event bus  
  
1. Edit the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BTSNTSvc.exe.config file.  
  
2. Locate the \<system.diagnostics\> and \</system.diagnostics\> tag. If they are not present in the file, copy the code listed above and paste it into the configuration file.  
  
3. Uncomment the Uncomment the system diagnostics section by moving the end comment delimiter ('-->') from after the \</system.diagnostics\> tag to before the \<system.diagnostics\> tag.  
  
4. Save the file.  
  
## Enabling Tracing for the BAM Portal  
 Enabling tracing for the BAM portal allows you to troubleshoot connectivity issues.  
  
 The BAM portal is an ASP.NET application, and follows the standard protocol for tracing. Within the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config file, there is a section called \<trace\> which you can enable.  
  
#### To enable tracing for the BAM portal  
  
1. Edit the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config file.  
  
2. Locate the \<system.diagnostics\> and \</system.diagnostics\> tags.  
  
3. Uncomment the system diagnostics section by moving end comment delimiter ('-->') from after the \</system.diagnostics\> tag to before the \<system.diagnostics\> tag.  
  
4. Modify the initializeData attribute to specify the location to write the tracing log.  
  
5. Locate \<system.web\> tag.  
  
6. In the system.web section locate the trace tag and uncomment the trace command by moving the delimiter ('-->') from after the trace tag to before it.  
  
7. Save the file.  
  
   `<!--`  
  
   `TRACING: To turn tracing on:`  
  
   `1) Uncomment this tag and specify a file path for trace output`  
  
   `2) Uncomment the <trace tag> under <system.web>`  
  
   `The trace will be saved to the file pointed to by "initializeData" below.`  
  
   `Ensure that the target directory exists (C:\temp by default).`  
  
   `Make sure that the IIS worker process user account (usually Network Service or ASPNET)`  
  
   `and the BAM Portal user have write permissions for the trace log file directory (C:\temp below).`  
  
   `To turn tracing on, you will need to uncomment the <trace> tag under <system.web>`  
  
   `<system.diagnostics>`  
  
   `<trace autoflush="true" indentsize="2">`  
  
   `<listeners>`  
  
   `<add name="BAMPortalListener"`  
  
   `type="System.Diagnostics.TextWriterTraceListener"`  
  
   `initializeData="C:\temp\BAMPortalTrace.log" />`  
  
   `</listeners>`  
  
   `</trace>`  
  
   `</system.diagnostics>`  
  
   `-->`  
  
   `<!--`  
  
   `TRACING: To turn tracing on:`  
  
   `1) Uncomment this tag`  
  
   `2) Uncomment the <system.diagnostics> tag above and specify a file path for trace output`  
  
   `<trace enabled="true"`  
  
   `requestLimit="40"`  
  
   `pageOutput="false"`  
  
   `traceMode="SortByTime"`  
  
   `localOnly="true"`  
  
   `writeToDiagnosticsTrace="true" />`  
  
   `-->`  
  
## BAM Alerting  
 Enabling tracing for BAM alerting helps you troubleshoot alert delivery failures.  
  
 BAM alerting is built on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services infrastructure. To enable tracing on BAM alerting, see the Notification Services troubleshooting topics at [http://go.microsoft.com/fwlink/?LinkId=79416](http://go.microsoft.com/fwlink/?LinkId=79416).  
  
## BAM Interceptors  
 To enable end-to-end tracing of the BAM interceptors, you modify the application’s configuration file—either Web.config for Web-hosted applications, or Appname.config for self-hosted applications. The following is an example of how you can modify the file:  
  
```  
<system.diagnostics>  
  </sources>  
    <source name="Microsoft BizTalk Bam Interceptors" switchValue="All">  
      <listeners>  
  
        <add name="myListener"  
             type="System.Diagnostics.TextWriterTraceListener"  
             initializeData="TextWriterOutput.log" />  
      </listeners>  
    </source>  
  </sources>  
</system.diagnostics>  
```  
  
 BAM Interceptor for Windows Workflow Foundation and Windows Communication Foundation are written to the source named "Microsoft BizTalk Bam Interceptors".  
  
> [!NOTE]
>  The source string is case-sensitive and must appear exactly as shown. If your string is different than the one shown, you will not receive trace information for the BAM interceptors.  
  
 You control the tracing level by setting switchValue. The available tracing levels are summarized in the following table.  
  
|Trace Level|Description|  
|-----------------|-----------------|  
|Critical|Logs Fail-Fast and Event Log entries, and trace correlation information.|  
|Error|Logs all exceptions.|  
|Warning|A condition exists that may subsequently result in an error or critical failure.|  
|Information|Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated. You can utilize such information for capacity planning and performance management.|  
|Verbose|Debug-level tracing for both user code and servicing.|  
|All|All messages.|  
  
> [!NOTE]
>  Tracing can have an adverse affect on performance. Only enable tracing when you are performing troubleshooting activities.  
  
### Viewing the WCF Trace File  
 To analyze the WCF trace you use the WCF Service Trace Viewer Tool. For more information about the Service Trace Viewer Tool, see [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)