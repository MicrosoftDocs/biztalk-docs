---
description: "Learn more about: How to Recover BAM Alerts"
title: "How to Recover BAM Alerts"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Recover BAM Alerts
As a part of recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], if you are using Business Activity Monitoring (BAM), you must also recover the BAM alerts.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.  
  
### To recover BAM alerts (SQL Server 2008)  
  
1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.  
  
2.  At the command prompt, type:  
  
     **nscontrol register -name BamAlerts -server**  *\<ServerName\>*  **-service -serviceusername "** *\<ServiceUserName\>* **" -servicepassword "** *\<ServicePassword\>* **"**  
  
     This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service computer by nscontrol).  
  
    > [!IMPORTANT]
    >  Remember to use the new Notification Services databases server in the **-server** option when re-registering the service. In addition, you should use the same user name for the new Notification Services service as the old one.  
  
3.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
4.  At the command prompt, type: **net start NS$BamAlerts**.  
  
## See Also  
 [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)
