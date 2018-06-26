---
title: "Receive Inbound tRFC Calls from SAP using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tRFC calls, receiving using BizTalk Server"
  - "tRFCs, sample"
ms.assetid: 500eedea-3d27-478c-a64c-903a1fa2b02f
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Inbound tRFC Calls from SAP using BizTalk Server
A tRFC server call is a transactional RFC server call. The orchestration required to receive an RFC in a transactional context is similar to the orchestration to receive any other inbound RFC sent from an SAP system. However, you need to perform certain additional tasks to make sure the RFCs are received in a transactional context. For more information about receiving an inbound RFC from the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Receive Inbound RFC Calls from SAP by using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md). For more information about how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports receiving inbound tRFC calls from an SAP system, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
 Receiving an inbound tRFC sent from an SAP system is similar to receiving an inbound RFC, with the following differences:  
  
1. At design time, while generating the schema, make sure you select the tRFC from under the **TRFC** node.  
  
2. At run time, make sure you set the binding property **TidDatabaseConnectionString**. This property takes the connection string to connect to a SQL database to store the TID. A sample connection string would look like:  
  
   ```  
   Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
   ```  
  
    For more information about the binding property and how to set it, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
   > [!IMPORTANT]
   >  The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard installs a SQL script, SapAdapter-DbScript-Install.sql, which must be run by the SQL Server administrator to create a database and the database objects in SQL Server. The script is typically installed at *\<installation drive\>:Program FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]*.  
   > 
   >  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses these objects to persist the TIDs. So, the SQL Server administrator must ensure that the user name provide as part of the connection string has sufficient privileges to execute the stored procedures. You can also opt for Windows authentication provided the Windows user has sufficient permissions to execute stored procedures in the database.  
  
3. Make sure MSDTC is enabled on the computer where the adapter is installed. Perform the following steps to enable MSDTC.  
  
   1.  Start the Component Services MMC snap-in.  
  
   2.  In the Component Services MMC snap-in, from the left pane expand **Component Services**, expand **Computers**, right-click **My Computer**, and click **Properties**.  
  
   3.  In the **My Computer Properties** dialog box, click the **MSDTC** tab.  
  
   4.  In the **Transaction Configuration** section, click the **Security Configuration** button.  
  
   5.  In the **Security Configuration** dialog box, select the **Network DTC Access** check box and within that, select the **Allow Remote Clients** check box.  
  
   6.  In the **Transaction Manager Communication** section, select the **Allow Inbound** and **Allow Outbound** check boxes.  
  
   7.  In the **Security Configuration** dialog box, click **OK**.  
  
   8.  Click **Yes** in the dialog box informing that the MSDTC service will be restarted. After the MSDTC service is restarted, click **OK** on the dialog box.  
  
   9. In the **My Computer Properties** dialog box, click **OK**.  
  
4. Add MSDTC to the Windows Firewall exception list, if not already added. Run the following command.  
  
   ```  
   netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
   ```  
  
> [!IMPORTANT]
>  An inbound tRFC call is used while receiving IDOCs from the SAP system in a "transactional" context.  
  
## See Also  
[Develop BizTalk applications](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)