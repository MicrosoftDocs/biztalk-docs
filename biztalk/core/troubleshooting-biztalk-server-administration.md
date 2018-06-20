---
title: "Troubleshooting BizTalk Server Administration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dfb56b0-352f-4012-b030-087bbcfe09d4
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting BizTalk Server Administration
This section provides a centralized location for information about common problems encountered while using the BizTalk Server Administration console.  
  
 In addition to the following Known Issues, [Common Issues and Resolutions With the BizTalk Server Administration Console](http://social.technet.microsoft.com/wiki/contents/articles/common-issues-and-resolutions-with-the-biztalk-server-administration-console.aspx) provides additional information.  
  
## Known Issues  
  
#### Delay in ENTSSO Service prevents BizTalk Server service from starting  
  
##### Problem  
 Rebooting your computer with DTC not set to automatic start-up may prevent the BizTalk Server service from starting.  
  
##### Cause  
 This is because the ENTSSO service can take more time to start than is allowed by the BizTalk Server service timeout duration.  
  
##### Solution  
 To resolve this issue, set DTC to automatic.  
  
#### SQL resources may become locked  
  
##### Problem  
 The following error may occur:  
  
 **Transaction (Process ID 95) was deadlocked on lock resources with another process and has been chosen as the deadlock victim. Rerun the transaction.**  
  
##### Cause  
 This is a very rare situation in which administrative operations performed by one user result in another user being locked out of database administration.  
  
##### Solution  
 The problem should remedy itself shortly. Try the operation again in a few minutes.  
  
#### SQL database may become locked  
  
##### Problem  
 Users may be locked out of the SQL database. A number of different error messages may be returned.  
  
##### Cause  
 In some cases one user writing to the database will effectively lock another user out of the database.  
  
##### Solution  
 The problem should remedy itself shortly. Try the operation again in a few minutes.  
  
#### Termination of multiple service instances in a multiple messagebox environment fails with an error  
  
##### Problem  
 Attempts to terminate multiple service instances from the BizTalk Server Administration console fail and an error similar to the following is displayed:  
  
 SQL Server blocked access to procedure 'sys.xp_sqlagent_enum_jobs' of component 'Agent XPs' because this component is turned off as part of the security configuration for this server.  
  
> [!NOTE]
>  This problem occurs in a multiple messagebox environment.  
  
##### Cause  
 This problem can occur in a multiple messagebox environment if the SQL agent job 'Operations_OperateOnInstances_OnMaster_\<*dbName*\>' is not running on the secondary messagebox databases. This job must be running in order to propagate information from the secondary messagebox databases to the primary messagebox database. This job will fail to run if it is not enabled or if a logon failure occurs.  
  
##### Solution  
 If you are using the BizTalk Administration console to perform operations on multiple service instances simultaneously and your BizTalk Server environment is configured with multiple messagebox databases, verify that the SQL Server Agent job named 'Operations_OperateOnInstances_OnMaster_\<*dbName*\>' is enabled on all secondary (non-master) messagebox databases. Additionally, the SQL Server Agent service on the SQL Server computer that hosts the secondary messagebox databases must run as an account that is included in the BTS_SQLAGENT_USER database role of the secondary messagebox database.  
  
> [!NOTE]
>  \<*dbname*\> is a placeholder for the actual name of the BizTalk messagebox database.  
  
 Follow these steps to add the SQL Server Agent service account to the BTS_SQLAGENT_USER database role of the secondary messagebox database  
  
 **On SQL Server 2008**  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.  
  
2.  When prompted choose the **Server type** of **Database Engine** and enter or select the **Server name** that hosts the secondary messagebox database.  
  
3.  Click to expand **Databases**, click to expand the secondary messagebox database, click to expand **Security**, click to expand **Roles**, click to expand **Database Roles**, and then double-click the BTS_SQLAGENT_USER database role.  
  
4.  Click the **Add** button.  
  
5.  Click **Browse**, select a group that the SQL Server Agent service account is a member of, and then click **OK**.  
  
> [!NOTE]
>  If the SQL Server Agent service account is not a member of the specified group then you will need to add it to the group.  
  
#### Changes applied in one instance of the BizTalk Administration console are not automatically updated in other instances of the BizTalk Administration console  
  
##### Problem  
 If multiple instances of the BizTalk Administration console are simultaneously connected to the same BizTalk Server group, changes made in one instance of the BizTalk Administration console are not automatically reflected in the other instance(s) of the BizTalk Administration console. This can cause concurrency violation errors when attempting to modify an artifact displayed in an instance of the BizTalk Administration console if the state of the artifact does not match the actual state of the artifact as stored in the BizTalk management database.  
  
##### Cause  
 Each instance of the BizTalk Administration console maintains its own cache of the BizTalk group configuration and only reflects changes in the cache. The cache is only updated when the BizTalk Administration console view is refreshed.  
  
##### Resolution  
 If you receive concurrency violation errors in the BizTalk Administration console, update the cache for the instance of the BizTalk Administration console by clicking the **Refresh** button on the BizTalk Administration console toolbar or by pressing the **F5** key.  
  
#### Failed to execute action 'Stop' error occurs when you attempt to stop an Orchestration with the BizTalk Administration console  
  
##### Problem  
 When you attempt to stop an Orchestration in the BizTalk Administration console, an error message similar to the following is generated:  
  
```  
Failed to execute action 'Stop'.  
------------------------------  
ADDITIONAL INFORMATION:  
A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.) (Microsoft SQL Server, Error: 10054)  
```  
  
 This problem may occur if the following conditions are true:  
  
-   The BizTalk Administration console is open.  
  
-   The BizTalk management database is installed on a clustered instance of SQL Server.  
  
-   The clustered instance of SQL Server is failed over.  
  
-   After the failover is complete, you attempt to stop a running instance of an orchestration using the BizTalk Administration console.  
  
##### Cause  
 The BizTalk Administration console maintains a connection to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database. When the connection to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database has been broken during the failover, some management tasks may return a "Failed to connect" or "Failed to execute" error until the BizTalk Administration console has been closed and reopened.  
  
##### Resolution  
 Close and reopen the BizTalk Administration console. When the BizTalk Administration console is reopened it creates a new connection to the specified [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database.  
  
#### Windows group names that were previously deleted do not have access to the BizTalk Server databases  
  
##### Problem  
 If, when reinstalling [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you use a Windows group name that was previously deleted, the Windows group will not have access to the BizTalk Server databases.  
  
##### Cause  
 Deleting a Windows group and then creating a Windows group with the same name produces a new Security Identifier (SID) for the Windows group. However the old SID is still cached in SQL Server, so the new Windows group cannot log on to SQL Server.  
  
##### Resolution  
 When you delete the Windows group, you must also remove the SQL Server login for the Windows group.  
  
#### BizTalk Administrator cannot start the BizTalk Server Administration console  
  
##### Problem  
 A BizTalk Administrator (member of the BizTalk Administrators Windows group) may not be able to open the BizTalk Server Administration console if that user is not a member of the Windows Administrators group on the local computer.  
  
##### Cause  
 This problem can occur if you have reinstalled or reconfigured BizTalk Server. This is because SQL Server used cached security IDs.  
  
##### Resolution  
 Temporarily add the BizTalk Administrator to the local Windows Administrators group on the local computer. After successfully opening the BizTalk Server Administration console, remove the BizTalk Administrator from the local Windows Administrators group on the local computer.  
  
#### Cannot start a host instance on a remote computer  
  
##### Problem  
 When you create a BizTalk Host instance on a remote computer, you may see the following error when you start the BizTalk Host instance: "Failed to start due to logon failure."  
  
##### Cause  
 This error can occur if you entered invalid credentials for the service account under which the BizTalk Host instance is running, or the service account does not have logon as service rights.  
  
##### Resolution  
 Assign logon as a service right to the service account in the remote computer before you start the BizTalk Host instance. This is done automatically on a local computer, but must be done manually on a remote computer.  
  
#### Creating or configuring a host instance on an X64 computer with the 32-bit only option selected fails  
  
##### Problem  
 In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, creating a BizTalk Host instance on an X64 computer with the 32-bit only option selected (default) may fail.  
  
 In BizTalk Server Configuration Manager, when configuring the BizTalk Server Runtime on an X64 computer, creating an in-process or isolated host instance with the 32-bit only option selected can cause the service to fail to start.  
  
##### Cause  
 Unknown  
  
##### Resolution  
 This issue is intermittent. Attempt to create or configure the host again or deselect the 32-bit only option.  
  
#### Host instance deletion does not clear registry information  
  
##### Problem  
 If you are not an administrator on the local computer, when you delete an in-process or isolated host, an access denied error message appears. You can forcibly delete the host. However, deleting the host in this manner does not clear all of the related registry information.  
  
##### Cause  
 Deletion of the registry information related to a host instance requires Administrator privileges.  
  
##### Resolution  
 Log on as a local Administrator account before deleting the host so that the related registry information is also removed.  
  
#### Cannot delete a MessageBox database  
  
##### Problem  
 You may not be able to delete a MessageBox database. If the deletion fails, one of the following issues may be responsible:  
  
- The cache refresh interval has not expired.  
  
- The MessageBox database contains incomplete instances.  
  
  If the cache refresh interval has not yet expired, the following error message appears when the deletion fails: "MessageBox cannot be deleted since there could be remaining work in the MessageBox. Please ensure that there are no more incomplete instances in the MessageBox, and try again."  
  
##### Cause  
 The cache refresh interval must expire between the time you disable new message publication in the MessageBox database and the time you delete the database. By default, the cache refresh interval is 60 seconds.  
  
##### Resolution  
 To delete a MessageBox database, you must first disable new message publication for that MessageBox database, and then wait until the cache refresh interval expires, before you delete the MessageBox database.  
  
 If the MessageBox database contains incomplete service instances, the following error message appears: "The MessageBox cannot be deleted because it may still contain incomplete instances. Ensure that there are no incomplete instances in the MessageBox, and try again".  
  
 You can view incomplete service instances in the MessageBox database using the Group Hub page in the BizTalk Server Administration Console. For information about viewing the status of service instances in the Group Hub page, see [How to Search for Tracked Service Instances](../core/how-to-search-for-tracked-service-instances.md).  
  
## See Also  
 [Troubleshooting](../core/troubleshooting.md)