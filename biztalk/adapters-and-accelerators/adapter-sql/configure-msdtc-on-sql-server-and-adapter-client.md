---
title: "Configure MSDTC on SQL Server and adapter client | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c87f455-a8c4-4169-bf18-695926136df1
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure MSDTC on SQL Server and adapter client
The operations performed on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] (through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the WCF service model, or the WCF channel model) can be performed within a transaction scope. If the client program has more than one transactional resource as part of the same transaction, the transaction gets elevated to an MSDTC transaction. To enable the adapter to perform operations within the scope of an MSDTC transaction, you must configure MSDTC both on the computer running the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and SQL Server. Also, you must add MSDTC to the exceptions list of Windows Firewall. This section provides information about how to perform these tasks on computers running the adapter client and SQL Server.  
  
> [!NOTE]
>  Performing operations on SQL Server using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] always involves two resources—the adapter connecting to SQL Server and the BizTalk Message Box residing on SQL Server. Hence, all operations performed using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] are performed within the scope of an MSDTC transaction. So, to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always enable MSDTC.  
> 
> [!NOTE]
>  For operations where the adapter client does not write any data to the SQL Server database, such as a Select operation, you might not want the additional overhead of performing the operations inside a transaction. In such cases, you can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform operations without a transactional context by setting the **UseAmbientTransaction** binding property to **false**. For more information about the binding property, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). In such cases, you do not need to configure MSDTC as well.  
  
## Configure MSDTC  
  
1. Open **Component Services**.  

   Or, In **Server Manager**, select **Tools**, and then select **Component Services**.  
  
2. Expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and select **Properties**.  
  
3. Select the **Security** tab. In this tab, select all of the following: 

   - **Network DTC Access**
   - **Allow Remote Clients** 
   - **Allow Inbound** 
   - **Allow Outbound** 
   - **No Authetnication Required**
  
4. Select **OK** to save your changes.  
  
5. If prompted to restarted the MSDTC service, select **Yes**. After the MSDTC service is restarted, close the properties and the Component Services MMC. 
  
## Add MSDTC to Windows Firewall exceptions list  

> [!TIP] 
>  Microsoft Distributed Tansaction Coordinator (MSDTC) may already be allowed in your firewall. If so, it is listed as an Inbound Rule. If it's not listed, use this section to allow MSDTC. 

1.  Open **Windows Firewall**, and select **Advanced Settings** on the left.  

    Or, In **Server Manager**, select **Tools**, and then select **Windows Firewall with Advanced Security**.  
  
2.  Right click **Inbound Rules**, and select **New Rule**.  
  
3.  In the wizard: 

    1. Select **Program**, and select **Next**. 
    2. Set the **program path** to `%SystemRoot%\system32\msdtc.exe`, and select **Next**.  
    3. **Allow the connection**, and select **Next**.
    4. Select **Domain**, and select **Next**.
    5. Enter any name, such as `MSDTC for Oracle EBS`, and select **Finish**.
  
5.  Complete the wizard, and close Windows Firewall. 
  
## See Also  
[Develop your SQL applications](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)