---
description: "Learn more about: Configuring Trace Listeners"
title: "Configuring Trace Listeners"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Trace Listeners
The DRDA Service supports multiple concurrent trace listeners, including the default Text Encoder, default Console Encoder, and optional Custom Encoder. The **drdaServiceTraceListeners** element contains one or more **drdaServiceTraceListener** elements to instruct the DRDA Server to send trace output to optional custom text trace listeners.  
  
## System Diagnostics  
 The DRDA Service supports a set of shared listeners to log information to text, console, and event log. The system.diagnostics element of the hostIntegration.drdaAs.drdaService section of the MsDrdaService.exe.config file defines and controls the various listeners.  
  
### App Config  
 Example of MsDrdaService.exe.config elements, attributes and values to enable the text and console trace listeners.  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="DrdaAs" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch">  
      <listeners>  
        <!--<add name="DrdaAsTextListener" />  
        <add name="DrdaAsConsoleListener" />  
        <add name="DrdaETWListener"/>  
        <add name="EventLog" />  
        -->  
        <remove name="Default" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="DrdaAsTextListener"  
          type="Microsoft.HostIntegration.Drda.Common.DrdaTraceListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"  
          initializeData="MsDrdaService.DSTF"  
          traceOutputOptions="None"  
          autoFlush="true"  
          traceLevel="0"  
          maxTraceEntries="1000000"   
          maxTraceFiles="10"  
         />  
    <add name="DrdaAsConsoleListener"  
         type="Microsoft.HostIntegration.Drda.Common.DrdaConsoleTraceListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"   
         traceOutputOptions="None"  
         traceLevel="3"   
         />  
    <add name="EventLog"  
          type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          initializeData="DrdaService1" >  
      <filter type="System.Diagnostics.EventTypeFilter"  
              initializeData="Error,Warning,Information"/>  
    </add>  
    <add name="DrdaETWListener"  
      type="Microsoft.HostIntegration.Drda.Common.DrdaEventProviderTraceListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"  
             initializeData="{3B4388CE-50E0-404C-A62B-E9C87D4F3BC4}"  
             traceLevel="0"/>  
  </sharedListeners>  
</system.diagnostics>  
```  
  
### Enabling Tracing  
 By default, the DRDA Service trace listeners are disabled. To enable the DRDA Service trace listeners, uncomment one or more elements in the source element within the system.diagnostics portion of the MsDrdaService.exe.config file. Also, to enable tracing, set a positive value (1-4) for the traceLevel attribute for each of the target trace listeners within the sharedListeners element of the system.diagnostics portion of the MsDrdaService.exe.config file.  
  
```  
<sources>  
  <source name="DrdaAs" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch">  
    <listeners>  
      <!--<add name="DrdaAsTextListener" />-->  
      <!--<add name="DrdaAsConsoleListener" />-->  
      <add name="DrdaETWListener"/>  
      <add name="EventLog" />  
      <remove name="Default" />  
    </listeners>  
  </source>  
</sources>  
```  
  
 Example of sources element in the system.diagnostics section of the MsDrdaService.exe.config file  
  
### Text Trace Listener  
 The DRDA Service text trace listener outputs trace data to a disk file.  
  
#### Trace Listener Name  
 The **name** attribute defines the name of the DRDA Service text trace listener. This **required** attribute is accepts a **string**, with a value of **DrdaAsTextListener** only.  
  
#### Trace Listener Type  
 The **type** attribute defines the type of the DRDA Service text trace listener. This **required** attribute is accepts a **string**, with a value of Microsoft.HostIntegration.Drda.Common.DrdaTraceListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL only.  
  
#### Trace Listener Initialization  
 The **initializeData** attribute defines the type of disk file to create. This **required** attribute is accepts a **string**, with a value of **MsDrdaService.DSTF** only.  
  
#### Trace File Folder  
 The **traceFileFolder** attribute instructs the DRDA Service where to write the text listener trace output file. This **optional** attribute accepts a **string** value. The default value is **C:\Program Files\Microsoft Host Integration Server 2013\traces**.  
  
> [!NOTE]
>  Each user account must have write access to the traces folder, in order to insert lines into the text trace file. Each user account requires the Folder Access Control List settings associated with the HIS Runtime Users Local Group. See section titled Security and Protection for more information.  
  
#### Automatic Flush  
 The **autoFlush** attribute instructs the DRDA Service to flush data automatically to the trace listener. This optional attribute accepts a **Boolean** value. The default is **true**.  
  
> [!NOTE]
>  The DRDA Service can flush trace data automatically to the trace listeners, which ensures the trace data is captured but will increase disk I/O and reduce overall system performance. To improve performance, set autoFlush=false, to disable automatic trace flush.  
  
#### Maximum Trace Entries  
 The **maxTraceEntries** attribute instructs the DRDA Service to trace up to a maximum number of entries, and then to stop tracing. This **optional** attribute accepts an **integer**. The default value is **1000000**.  
  
#### Trace Output Options  
 The **traceOutputOptions** attribute is not used by the DRDA Service. This **optional** attribute accepts a **string** value. The default value is **none**.  
  
#### Trace Level  
 The **traceLevel** attribute instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This **optional** attribute accepts an **integer** value. The default value is **0**, which disables tracing.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Output no tracing messages.|  
|1|Output error messages.|  
|2|Output warning messages and error messages.|  
|3|Output information messages, warning messages and error messages.|  
|4|Output all messages.|  
  
 *DRDA Service trace listener levels.*  
  
### Console Trace Listener  
 The DRDA Service console trace listener outputs trace data to a command console window.  
  
#### Trace Listener Name  
 The **name** attribute defines the name of the DRDA Service text trace listener. This **required** attribute is accepts a **string**, with a value of **DrdaAsConsoleListener** only.  
  
#### Trace Listener Type  
 The **type** attribute defines the type of the DRDA Service text trace listener. This **required** attribute is accepts a **string**, with a value of Microsoft.HostIntegration.Drda.Common.DrdaConsoleTraceListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL only.  
  
#### Trace Output Options  
 The **traceOutputOptions** attribute is not used by the DRDA Service. This **optional** attribute accepts a **string** value. The default value is **none**.  
  
#### Trace Level  
 The **traceLevel** attribute instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This **optional** attribute accepts an **integer** value. The default value is **3**, which disables tracing.  
  
### ETW Trace Listener  
 The DRDA Service ETW (Event Tracing for Windows) trace listener as an ETW provider outputs trace data through an ETW session to a Windows operating system ETW controller. An administrator can register the ETW provider using the ProviderId GUID “3B4388CE-50E0-404C-A62B-E9C87D4F3BC4”. An ETW consumer can read ETW log files or listen to an ETW session for real time events.  
  
#### Trace Listener Name  
 The **name** attribute defines the name of the DRDA Service text trace listener. This **required** attribute is accepts a **string**, with a value of **DrdaETWListener**.  
  
#### Trace Listener Type  
 The **type** attribute defines the type of the DRDA Service ETW trace listener. This **required** attribute is accepts a **string**, with a value of Microsoft.HostIntegration.Drda.Common. DrdaEventProviderTraceListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL only.  
  
#### Trace Listener Initialization  
 The **initializeData** attribute defines the ETW ProviderID GUID used to register the ETW provider to the ETW controller. This **required** attribute is accepts a **string**, with a value of **3B4388CE-50E0-404C-A62B-E9C87D4F3BC4**.  
  
#### Trace Level  
 The **traceLevel** attribute instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This **optional** attribute accepts an **integer** value. The default value is **0**, which disables tracing.  
  
### Event Log Listener  
 The DRDA Service event log listener outputs log data to the Windows event log.  
  
### Event Log Listener Name  
 The **name** attribute defines the name of the DRDA Service event log listener. This **required** attribute is accepts a **string**, with a value of **EventLog**.  
  
### Event Log Listener Type  
 The **type** attribute defines the type of the DRDA Service event log listener. This **required** attribute is accepts a **string**, with a value of System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
  
### Event Log Listener Initialization  
 The **initializeData** attribute defines the DRDA Server service instance. This **required** attribute is accepts a **string**, with a value of **DrdaService1**.  
  
### Event Log Listener Filter  
 The **filter** element instructs the DRDA Service to log data by filter type. This required element contains two attributes: type; and initializData.  
  
### Event Log Filter Type  
 The **type** attribute of the filter element defines a filter type. This **required** attribute accepts a **string** value, with a value of **System.Diagnostics.EventTypeFilter**.  
  
### Event Log Filter Level  
 The **initializeData** attribute instructs the DRDA Service to log defined collections of information. This **optional** attribute accepts a **string** value. The default value is **Error,Warning,Information**, which includes all event log levels.  
  
|Value|Description|  
|-----------|-----------------|  
|Error|This value instructs the DRDA Service to log only the error level data.|  
|Warning|This value instructs the DRDA Service to log only the warning level data.|  
|Information|This value instructs the DRDA Service to log only the information level data|  
  
 *DRDA Service event log listener levels.*  
  
### Custom Trace Listener  
 The DRDA Service supports custom trace listeners in the form of a .NET Framework custom listener. See Programmer’s Guide and Reference for information on the custom trace listener sample. The **drdaServiceTraceListeners** element contains one or more **drdaServiceTraceListener** elements to instruct the DRDA Server to send trace output to optional custom text trace listeners. The **drdaServiceTraceListener** element contains a set of attributes to define a custom trace listener. The type is Microsoft.HostIntegration.Drda.Common.BaseDrdaTraceListener, which defined a DRDA Server custom trace listener.  
  
 The DRDA Service will process text trace output to a custom trace listener that is referenced in the MsDrdaService.exe.config as follows.  
  
```  
<drdaServiceTraceListeners>  
          <drdaServiceTraceListener type="Microsoft.HostIntegration.Drda.Common.BaseDrdaTraceListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"  
                                    traceLevel="4"/>  
        </drdaServiceTraceListeners>  
```  
  
 Default values for custom trace listener in the DRDA Service application configuration file.  
  
#### Trace Level  
 The **traceLevel** attribute instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This **optional** attribute accepts an **integer** value. The default value is **0**, which disables tracing.  
  
#### Settings  
 The **settings** attribute instructs the DRDA Service to pass information to the custom bind listener. This **optional** attribute accepts a **string** value. The default value is **none**.
