---
description: "Learn more about: How to Configure Host Print Service for an IBM System i Computer"
title: "How to Configure Host Print Service for an AS-400 Computer1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure Host Print Service for an IBM System i Computer
Configuring IBM System i print service involves the following steps:  
  
-   Creating Link Services  
  
-   Creating Connections  
  
-   Creating LUs  
  
### To create a print LU  
  
1.  In SNA Manager, expand **SNA Service** for the server that you are working with, and then expand **Connections**.  
  
2.  Right-click the appropriate connection, point to **New**, and then click **Printer LU**.  
  
3.  Define your printer LU. You can keep the default for the **LU Number** or assign your own. Although the LU number is meaningful to the connection itself, the number is not very useful, so you can add a user-friendly name in the **LU Name** box.  
  
4.  Click **OK**.  
  
### To configure Host Print service for an IBM System i Connection  
  
1. In SNA Manager, expand the server on which you want to add print services.  
  
2. Right-click **Print Service**, point to **New**, and then click **APPC Session**.  
  
3. The **Properties** page for this session appears.  
  
4. On the **General** tab, type a session name, click **Printer**, and then configure a printer.  
  
5. On the **APPC** tab, provide an **IBM System i Device Name**, a **Local LU Alias**, a **Mode Name**, and a **Remote LU** to use for this print session.  
  
6. If the **IBM System i Device Name** you specify does not exist on the IBM System i, it will be created.  
  
7. On the **Security** tab, configure security for this print session.  
  
8. Configure other parameters as desired.  
  
9. Click **OK** to add this print session.  
  
10. In the console tree, right-click **Print Service**, and then click **Save Configuration**.  
  
11. Right-click **Print Service** again, and then click **Start**.  
  
    The Print Service feature of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] supports print jobs from an IBM System i that contain basic formatting options. Some print jobs require special formatting. To properly print these jobs, the Host Print Transform feature of the IBM System i must be enabled. Host Print Transform is a feature of the IBM System i operating system (V3R1 and later) that translates print jobs in the SNA character string (SCS) data stream into an ASCII data stream (such as PCL). The data stream is specific to a particular make and model of ASCII printer, which must be defined at the time Host Print Transform is enabled.
