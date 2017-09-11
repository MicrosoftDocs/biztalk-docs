---
title: "Using MQSeries Adapter with an Earlier Version of the Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQSeries adapters, compatibility"
ms.assetid: 278a13ff-8e46-4af4-a76e-b6d4aad5b768
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using MQSeries Adapter with an Earlier Version of the Adapter
The [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)], [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], and [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] versions of the MQSeries adapter can all work with the same remote WebSphere MQ Server on Windows. This is possible because the following versions of the COM+ applications used with the MQSeries adapter can coexist on the same WebSphere MQSeries computer:  
  
-   **MQSAgent (MQSAgent2) COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)].  
  
-   **MQSAgent COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)].  
  
-   **MQHelper COM+ application** used with the MQSeries Adapter for [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)].  
  
> [!NOTE]
>  When configuring a side-by-side installation of these COM+ applications, ensure that none of these COM+ applications are configured to use the same MQSeries queues.  
  
> [!IMPORTANT]
>  Side-by-side installation of the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] version of the MQSeries Adapter COM+ application with an earlier version of the MQSeries Adapter COM+ application is only supported if an earlier version of BizTalk Server is not installed on the WebSphere MQSeries computer.  
  
### To install the BizTalk Server 2006 version of the MQSeries Adapter COM+ application on a WebSphere MQSeries computer that is running an earlier version of the MQSeries Adapter COM+ application  
  
1.  Run the Bootstrap.msi from the \Platform\BootStrap\ directory of the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] CD to copy the dependency files MSVCR80.dll and MSVCP80.dll to the WebSphere MQSeries computer.  
  
2.  Copy the file MQSAgent.dll from the \Msi\Program Files\ directory on the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] CD to the WebSphere MQSeries computer.  
  
    > [!NOTE]
    >  Also copy the file MQSTrace.cmd from this directory to the WebSphere MQSeries computer if you plan on using the MQSAgent tracing utility. For more information about the MQSAgent tracing utility see [Analyzing MQSeries Adapter Errors with the Trace Tools](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).  
  
3.  Manually register the components in MQSAgent.dll by running regsvr32 mqsagent.dll on the WebSphere MQSeries computer:  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  Run this command from the same directory that you copied MQSAgent.dll to.  
  
4.  Create a new COM+ application for the MQSAgent components:  
  
    -   Right-click COM+ Applications, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.  
  
    -   Click **Create an empty application**.  
  
    -   Enter the name **MQSAgent2**, leave the default option for **Server application** enabled and click **Next**.  
  
    -   Select the option for **This user**, enter the appropriate account information and click **Next**.  
  
        > [!NOTE]
        >  This account should have connect and put and/or get permissions on the appropriate IBM WebSphere MQ queues.  
  
    -   Click **Next** on the Add **Application Roles** dialog box.  
  
    -   Click **Next** on the **Add Users to Roles** dialog box.  
  
    -   Click **Finish**.  
  
5.  Add the MQSAgent.dll components to the MQSAgent2 COM+ application:  
  
    -   Click to expand the **MQSAgent2** COM+ Application.  
  
    -   Right-click **Components** and click **New**, **Component** to launch the COM+ Component Install Wizard and then click **Next**.  
  
    -   Click **Install New Components**, browse to the file MQSAgent.dll and then click **Open**.  
  
    -   Click **Next**, and then click **Finish**.  
  
## See Also  
 [Using the MQSeries Adapter](../core/using-the-mqseries-adapter.md)