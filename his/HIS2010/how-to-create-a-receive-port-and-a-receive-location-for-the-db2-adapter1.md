---
title: "How to Create a Receive Port and a Receive Location for the DB2 Adapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a648055a-dd79-4a11-8da1-837a8ec10aee
caps.latest.revision: 5
---
# How to Create a Receive Port and a Receive Location for the DB2 Adapter
You create a receive port and receive location for the BizTalk Adapter for DB2 by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions in the Single Sign-On (SSO) database.  
  
### To configure a receive port and a receive location  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft BizTalk Server 2006**, and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Group**, expand **Applications**, and then select the application for which you want to create a send port.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **Static One-way Receive Port**.  
  
     The **Receive Port Properties** dialog box appears.  
  
4.  Configure the properties and then click **OK**.  
  
     For more information, click **Help**.  
  
5.  In the console tree, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
     The **Select a Receive Port** dialog box appears.  
  
6.  Select the receive port you created in step 3, and then click **OK**.  
  
     The **Receive Location Properties** window appears.  
  
7.  In the **Transport Type** field, select **DB2**, and then click **Configure**.  
  
     The **DB2Transport Properties** dialog box appears.  
  
8.  Configure the following properties:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Connection String**|Enter the name of a connection string that will be used to connect to the DB2 database.<br /><br /> To configure a new or existing Connection String, click the ellipsis (**…**). This starts the Data Source Wizard. To access Help, click **Help** on the wizard pages, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (DB2)](../HIS2010/data-source-wizard-db2-1.md).|  
    |**Document Root Element Name**|The root element name that is used in the XML documents that are received from DB2.|  
    |**Document Target Namespace**|The target namespace that is used in the XML documents that are received from DB2.|  
    |**SQL Command**|The select or stored procedure command that is executed one time for each polling interval.|  
    |**Update Command**|The command that is executed after each row in the receive operation is processed. It can be either a delete statement that deletes the row from the table in the SQL command, or an update command that statically modifies one or more rows. When this option is specified, the SQL command must be a Select statement and must access a single table.|  
    |**URI**|A name identifying the receive port location. Default is DB2://.|  
    |**Polling Interval**|The number of units between polling requests. Allowed range is 1 - 65535.|  
    |**Polling Unit of Measure**|The unit of measure (seconds, minutes, or hours) used between polling requests. Default is seconds.|  
    |**Message Batch Size**|When an SQL command returns a result set to the DB2 receive adapter, the adapter submits one message to the BizTalk message engine for each row in the result set. This is referred to as a single row receive. The receive adapter can optionally return the result set in its entirety as a single message to the BizTalk message engine. Messages can also have a fixed number of rows in them (for example, one message contains 10 rows). Default is -1.|  
  
9. Click **OK** to return to the **Receive Location Properties** dialog box.  
  
10. In the **Receive Handler** field, select the instance of the BizTalk Server host on which the receive location will run. The receive handler must be running on this host.  
  
11. In the **Receive Pipeline** field, select the receive pipeline to use to receive messages at this receive location.  
  
12. To configure a receive pipeline, click “**..**”. For more information, click **Help** on the property pages.  
  
13. To configure scheduling, click the **Schedule** tab.  
  
     For more information, click **Help** on the **Schedule** tab.  
  
14. When you are finished with configuration, click **OK** to close the **Receive Location Properties** dialog box and return to the BizTalk Server Administration console tree.  
  
15. In the **Receive Locations** window, right-click the receive location in the **Name** column and select **Enable**.  
  
## See Also  
 [BizTalk Adapter for DB2 Configuration](../HIS2010/biztalk-adapter-for-db2-configuration2.md)   
 [Data Access Library &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/da533736-8ecc-4466-a13d-b635696d94c8)   
 [Managed Provider for DB2 Programmer's Guide](../HIS2010/managed-provider-for-db2-programmer-s-guide1.md)   
 [Data Access Library Programmer's Guide &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/73ba0edf-74d4-44d5-b018-47f9f88dddf2)