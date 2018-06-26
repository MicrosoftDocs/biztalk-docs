---
title: "Configuring Host Print Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b109939-f252-4ede-8804-1f1ecfc8105c
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring Host Print Service
Configuring Host Print service involves the following steps:  
  
- Creating Link Services  
  
- Creating Connections  
  
- Creating a 3270 Printer LU  
  
- Configuring Host Print Service  
  
  In addition, a print demonstration using a script is available. The following procedures will create and configure the print demonstration:  
  
### Configuring Host Print service for a 3270 connection  
  
1. In SNA Manager, expand the server on which you want to add print services.  
  
2. Right-click **Print Service**, point to **New**, and then click **3270 Session**.  
  
3. The **Properties** page for this session appears.  
  
4. On the **General** tab, type a session name.  
  
5. Click **Printer**, and then configure a printer.  
  
6. Click the **3270** tab, choose an LU Name to use for this print session. If there are no LU names in the drop-down list, you will need to insert a printer LU on the 3270 connection to be used for this print session (To create a print LU, see the earlier procedure).  
  
7. Configure other parameters as desired.  
  
8. Click **OK** to add this print session.  
  
9. In the console tree, right-click **Print Service**, and then click **Save Configuration**.  
  
10. Right-click **Print Service** again, and then click **Start**.  
  
    The Host Print service is configured with startup set to Manual. To start the Host Print service at system startup, go to the **Services** icon of Control Panel. Select the service name. Click **Startup**. Change the service activation type from Manual (the default) to Automatic for this service.  
  
    SNA Manager will only lock the configuration file when you initiate a configuration change. If the lock is obtained, the status bar will flash **'CONFIG LOCK'**. When you complete the change and save the configuration file, the lock will be released and the status bar will be cleared. The status bar will display **'OUT OF DATE'** on other servers in the domain. To refresh the status on the **'OUT OF DATE'** servers, SNA Manager must be closed and reopened.  
  
## See Also  
 [Host Print Service Character Translation Table Format](../core/host-print-service-character-translation-table-format1.md)