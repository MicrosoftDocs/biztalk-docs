---
title: "Enabling EDI and AS2 Status Reports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa40fbad-51ad-40e0-9fe3-68e54beb11a5
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enabling EDI and AS2 Status Reports
This topic describes how to configure the EDI and AS2 status reports in the **Group Overview** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
 Status reporting tracking data is stored in the BizTalk tracking database (BizTalkDTADb) in accordance with the storage properties selected in the procedures below. You can configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to enable status reporting for each agreement. Depending upon the amount of data that you store, you should routinely archive the data from the active store and ultimately clean it out from the archival store, as appropriate. For more information about managing the BizTalkDTADb database, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).  
  
 You can enable status reports in three ways:  
  
- Enable status reports for inbound or outbound EDI interchanges that resolved to an agreement.  
  
- Enable status reports for EDI fallback agreement properties, so status reporting is activated for EDI interchanges that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] could not determine an agreement for.  
  
- Enable status reports for AS2 messages.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group or BizTalk Server B2B Operators group.  
  
### To enable EDI status reports for an agreement  
  
1. In the **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration** Console, click the **Parties** node under the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and **BizTalk Group** nodes.  
  
2. In the **Parties and Business Profiles** pane, click the party that has the X12 or EDIFACT agreement for which you want to enable status reporting.  
  
3. In the **Agreements** section, right-click the agreement for which you want to enable status reporting and then click **Properties**.  
  
4. In the **General** tab, in the **Common Host Settings** section, click **Turn ON Reporting**.  
  
   > [!NOTE]
   >  This step causes message entries to be entered in the status report UI in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
5. Select **Store transaction set/payload for reporting** to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.  
  
   > [!NOTE]
   >  If you enable storage of transaction sets while an instance of the batching orchestration is activated, transaction sets will not be stored for the batch being created. However, if you disable storage of transaction sets while an instance of the batching orchestration is activated, the storage will be disabled in the middle of the batching.  
  
6. Click **OK**.  
  
7. Restart the BizTalk Service (in the Computer Management dialog box). If the AS2EdiReceive pipeline or the AS2EdiSend pipeline is being used in your solution, restart the IIS Admin service (using the *iisreset* command), as well.  
  
   > [!NOTE]
   >  The BizTalk Service needs to be restarted after EDI status reporting has been activated or deactivated for the change to take effect. If the AS2EdiReceive or AS2EdiSend pipeline is being used in your solution, both the BizTalk Service and the IIS service need to be restarted for the change to take effect. Note that this is not necessary when enabling AS2 status reporting.  
  
### To enable EDI status reports for fallback agreements  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group** nodes, right-click **Parties**, and select **X12 Fallback Settings** or **EDIFACT Fallback Settings**.  
  
   > [!NOTE]
   >  When you configure status reports in the fallback agreements, the configuration only applies when no agreement has been determined for a message.  
  
2. In the **Fallback Settings General Pages** tab, click **Activate EDI reporting**.  
  
   > [!NOTE]
   >  This step causes message entries to be entered in the status report UI in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
3. Select **Store transaction set/payload for reporting** to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.  
  
   > [!NOTE]
   >  **For EDIFACT-encoded messages**: If you select this property, you must also select a value for the UNB3.2 field (Code qualifier) in the UNB Segment Definition page of the EDI Global Properties dialog box. This property is not set by default, and the interchange will be suspended if **Store transaction set/payload for reporting** is selected, but a value is not selected for UNB3.2.  
  
4. Click **OK**.  
  
### To enable AS2 status reports  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and **BizTalk Group** nodes, click the **Parties** node.  
  
2. In the **Parties and Business Profiles** pane, click the party that has the X12 or EDIFACT agreement for which you want to enable status reporting.  
  
3. In the **Agreements** section, right-click the agreement for which you want to enable status reporting and then click **Properties**.  
  
4. In the **Common Host Settings** section, click **Turn ON Reporting**.  
  
   > [!NOTE]
   >  This step causes message entries to be entered in the status report UI in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
5. In the one-way agreement tab of the **Agreement Properties** dialog box, click the **Receiver Message Tracking (NRR)** page.  
  
6. In the **Receiver Message Tracking (NRR)** page, click **NRR enabled for inbound encoded AS2 messages** to enable display of the wire format of incoming messages.  
  
   > [!NOTE]
   >  The wire format of the message will be displayed when you right-click the message in the AS2 Message and Correlated MDN Status Page, and then click **Message Wire Format**.  
  
   > [!NOTE]
   >  The **Turn ON Reporting** property must be selected for you to enable storage of any data in the non-repudiation database. If you select this or any of the other properties enabling storage in the non-repudiation database, a popup will be displayed prompting you to activate AS2 reporting. If you click **Yes**, AS2 reporting will be activated for you.  
  
7. In the **Receiver Message Tracking (NRR)** page, click **NRR enabled for inbound decoded AS2 messages** to enable display of the decoded format of incoming messages.  
  
8. In the **Receiver Message Tracking (NRR)** page, click **NRR enabled for outbound MDN** to enable display of MDN responses to incoming messages.  
  
9. In the one-way agreement tab of the **Agreement Properties** dialog box, click the **Sender Message Tracking (NRR)** page.  
  
10. In the **Sender Message Tracking (NRR)** page, click **NRR enabled for outbound encoded AS2 messages** to enable display of the wire format of outgoing messages.  
  
11. In the **Sender Message Tracking (NRR)** page, click **NRR enabled for outbound decoded AS2 messages** to enable display of the decoded format of outgoing messages.  
  
12. In the **Sender Message Tracking (NRR)** page, click **NRR enabled for inbound MDN** to enable display of MDN responses to outgoing messages.  
  
13. Click **OK**.  
  
## See Also  
 [Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md)   
 [Configuring an EDI and AS2 Status Report](../core/configuring-an-edi-and-as2-status-report.md)   
 [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md)   