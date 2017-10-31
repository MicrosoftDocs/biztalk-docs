---
title: "How to Create a Receive Port and a Receive Location for the Host File Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29769f4a-7318-446a-b7b9-d188b2badef7
caps.latest.revision: 4
---
# How to Create a Receive Port and a Receive Location for the Host File Adapter
You create a receive port and receive location for the BizTalk Adapter for Host Files by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions in the Single Sign-On (SSO) database.  
  
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
  
7.  In the **Transport Type** field, select **HostFiles**, and then click **Configure**.  
  
     The **HostFilesTransport Properties** dialog box appears.  
  
8.  Configure the following properties:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Connection String**|Enter the name of a connection string that will be used to connect to the host database.<br /><br /> To configure a new or existing connection string, click the ellipsis (**…**). This starts the Data Source Wizard. To access Help, click **Help** on the wizard screens, or open the [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (Host Files)](../core/data-source-wizard-host-files.md).<br /><br /> When configuring a receive location or send port based on the BizTalk Adapter for Host Files, the metadata definition should be created as a Host Integration Designer XML (HIDX) metadata file for encoding and decoding records. For instructions on how to create a HIDX file, see [Creating an Application with the Managed Data Provider for Host Files](../Topic/Creating%20an%20Application%20with%20the%20Managed%20Data%20Provider%20for%20Host%20Files1.md).|  
    |**Document Root Element Name**|The root element name that is used in the XML documents that are received from the host.|  
    |**Document Target Namespace**|The target namespace that is used in the XML documents that are received from the host.|  
    |**SQL Command**|The Select command that is executed one time for each polling interval.|  
    |**Update Command**|The command that is executed after each row in the receive operation is processed. It can be either a delete statement that deletes the row from the table in the SQL command, or an update command that statically modifies one or more rows. When this option is specified, the SQL command must be a Select statement and access a single table.<br /><br /> You can specify additional properties by clicking the ellipsis (**…**) button. This opens the **Change Command** dialog box, which provides three options:<br /><br /> -   **Do nothing** clears the other two options if selected.<br />-   **Delete after read** deletes the row after the adapter has read it.<br />-   **Update** lets you type an SQL command to be updated.|  
    |**URI**|Uniform resource identifier. A name identifying the receive port location.|  
    |**Polling Interval**|The number of units between polling requests. Allowed range is 1 - 65535.|  
    |**Polling Unit of Measure**|The unit of measure (seconds, minutes, or hours) used between polling requests. Default is seconds.|  
  
9. Click **OK** to return to the **Receive Location Properties** dialog box.  
  
10. In the **Receive Handler** field, select the instance of the BizTalk Host on which the receive location will run. The receive handler must be running on this host.  
  
11. In the **Receive Pipeline** field, select the receive pipeline to use to receive messages at this receive location.  
  
     To configure a receive pipeline, click “**..**”. For more information, click **Help** on the property pages.  
  
12. To configure scheduling, click the **Schedule** tab.  
  
     For more information, click **Help** on the **Schedule** tab.  
  
13. When you are finished with configuration, click **OK** to close the **Receive Location Properties** dialog box and return to the BizTalk Server Administration console tree.  
  
14. In the **Receive Locations** window, right-click the receive location in the **Name** column and select **Enable**.  
  
## See Also  
 [BizTalk Adapter for Host Files Configuration](../core/biztalk-adapter-for-host-files-configuration.md)   
 [Data Access Library &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/da533736-8ecc-4466-a13d-b635696d94c8)   
 [Managed Data Provider for Host Files](../Topic/Managed%20Data%20Provider%20for%20Host%20Files1.md)   
 [How to Create a Send Port for the Host File Adapter](../core/how-to-create-a-send-port-for-the-host-file-adapter.md)