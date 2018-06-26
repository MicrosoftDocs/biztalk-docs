---
title: "How to Turn Off Global Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eae3059a-cbdd-47c4-84cd-edfb5480b9fa
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Turn Off Global Tracking
By default, global tracking is enabled when you install BizTalk Server. The BizTalk Tracking (BizTalkDTADb) database grows in size as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes data on your system. If the size of the BizTalk Tracking database causes poor disk performance, you can purge the data from the Tracking database. If you are having performance issues that are momentarily addressed by purging the BizTalk tracking database, and you want to configure BizTalk to no longer collect tracking information, you may want to consider turning off global tracking.  
  
 It is important to understand that turning off global tracking disables the tracking interceptors for the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. This means that BizTalk will not track events in its tracking tables. Alternatively, you can turn off tracking for individual events.  
  
> [!NOTE]
>  If you are using Business Activity Monitoring (BAM), you should maintain a dedicated tracking host, even if you disable global tracking. This is because BAM events use the Tracking Data Decode Service (TDDS).  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To turn off global tracking (SQL Server 2008)  
  
1. On the SQL server that hosts the BizTalk Tracking (BizTalkDTADb) database, click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2. In the **Connect to Server** dialog box, verify the server name and authentication, and then click **Connect**.  
  
3. In Microsoft SQL Server Management Studio, in **Object Explorer**, expand \<*computer name*\>, expand **Databases**, expand **BizTalkMgmtDb**, expand **Tables**, right-click **adm_Group**, and then click **Open Table**.  
  
4. In the table viewer, scroll horizontally until you find **GlobalTrackingOption**.  
  
5. In the **GlobalTrackingOption** column, change the value from 1 to 0, to turn off this feature, and then press ENTER.  
  
6. Close Microsoft SQL Server Management Studio.  
  
   > [!NOTE]
   >  You must restart your BizTalk hosts for the change to take effect.  
  
7. Click **Start**, click **Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
8. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.  
  
9. In the details pane, right-click each host, and then click **Restart**.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)   
 [How to Purge Data from the BizTalk Tracking Database](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)   
 [How to Manually Purge Data from the BizTalk Tracking Database](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)