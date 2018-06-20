---
title: "Transactional Adapter (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31a13377-cc89-4763-ad1b-508a16fc9708
caps.latest.revision: 36
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transactional Adapter (BizTalk Server Sample)
The Transactional Adapter sample demonstrates how to create and use an explicit Microsoft Distributed Transaction Coordinator (MSDTC) transaction against a database during processing of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message.  

## What This Sample Does  
 This sample contains a receive adapter which runs a SQL statement at a user-specified interval to obtain data from a SQL Server database using an MSDTC transaction. The data is then submitted to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database in the form of a message under the context of the same transaction.  

 The corresponding send adapter runs a user-specified SQL stored procedure using input from a BizTalk message in the context of a transaction. It uses specific data from that message to locate and delete the corresponding message from the Message Box database under that same transaction.  

## How This Sample is Designed and Why  
 This sample has two projects in its solution. The first is the administrative project (Admin) which is used prior to runtime to allow a user to configure the receive locations and send ports that use this adapter. The second is the runtime project (Runtime) that runs when the send and receive adapters are executing.  

## Where to Find This Sample  
 The sample is located in the following SDK location:  

 \<*Samples Path*\>\Samples\AdaptersDevelopment\TransactionalAdapter. The administrative configuration project is located in the \Admin folder, while the runtime project exists in the \Runtime folder.  

 The following table shows the files in this sample and describes their purpose.  

|Admin Project Filename|Admin Project File Description|  
|----------------------------|------------------------------------|  
|TransactionalAdmin.csproj|Adapter administrative project file used for pre-runtime configuration|  
|TransactionalReceiveHandler.xsd|XSD for receive handler properties|  
|TransactionalReceiveLocation.xsd|XSD for receive location properties|  
|TransactionalTransmitLocation.xsd|XSD for transmit location properties|  
|TransactionalTransmitHandler.xsd|XSD for transmit handler properties|  
|TransactionalAdapterManagement.cs|Adapter configuration management. Contains GetConfigSchema which is invoked by the BizTalk Adapter Framework to return an XSD configuration schema for each of the (four) possible configuration types it supports.|  

|Runtime Project Filename|Runtime Project File Description|  
|------------------------------|--------------------------------------|  
|Transactional.csproj|Adapter runtime project file|  
|TransactionalAsyncBatch.cs|Asynchronous implementation of the send part of the adapter|  
|TransactionalDeleteBatch.cs|Deletes a batch of messages and votes to commit or abort a transaction|  
|TransactionalProperties.cs|Extracts and sets configuration properties|  
|TransactionalReceiver.cs|Creates and manages receive endpoints|  
|TransactionalReceiverEndpoint.cs|Actual listening or polling for each receive location|  
|TransactionalTransmitter.cs|Accepts a batch of messages from the Messaging Engine to be transmitted|  

## How to Use This Sample  
 This sample is meant as a framework for you to use in creating custom send and receive adapters using explicit transactions.  

## Building and Initializing This Sample  

> [!IMPORTANT]
>  If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.  

#### Create a Strong Name Key for the Transactional Adapter sample  

1.  Start **Visual Studio Command Prompt**.  

2.  At the command prompt, type the following and then press enter:  

    ```  
    cd \Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Runtime  
    ```  

3.  At the command prompt, type the following and then press enter:  

    ```  
    sn –k TransactionalAdapter.snk  
    ```  

4.  At the command prompt, type **exit**, and then press enter to close the command prompt window.  

#### Build the Transactional Adapter Solution  

1. Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.  

2. Browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter, and double-click **TransactionalAdapter.sln** to open this solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  

3. To build both of the Transactional Adapter projects (Admin and Runtime) in Solution Explorer, right-click **Solution TransactionalAdapter**, and then click **Rebuild**.  

## Running This Sample  

#### Register the Transactional Adapter  

1. In Windows Explorer, navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Admin.  

2. To add the transactional adapter data to the registry, double-click **TransactionalAdmin.reg**.  

   > [!NOTE]
   >  **TransactionalAdmin.reg** includes hard-coded paths to C:\Program Files\Microsoft BizTalk Server\\. If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the default location or if you upgraded your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from a previous version, you must modify the file TransactionalAdmin.reg with the appropriate paths. Update the paths associated with the "InboundAssemblyPath", "OutboundAssemblyPath", and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.  
   > 
   > [!IMPORTANT]
   >  If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **TransactionalAdmin.reg** registry file.  

3. In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.  

4. To close Windows Explorer, click **File**, and then click **Close**.  

#### Add the Transactional Adapter to BizTalk Server  

1. Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **BizTalk Server Administration** tree, expand the **BizTalk Group** tree, and then expand the **Platform Settings**  tree.  

3. Right-click **Adapters**, click **New**, and then click **Adapter**.  

4. In the **Adapter Properties** dialog box, do the following.  


   |  Use this   |                                                            To do this                                                             |
   |-------------|-----------------------------------------------------------------------------------------------------------------------------------|
   |    Name     |                                                  Type **TransactionalAdapter**.                                                   |
   |   Adapter   | Select **Txn** from the drop-down list. This entry appears as a result of running the **TransactionalAdmin.reg** file previously. |
   | Description |                                              Type **Sample Transactional Adapter**.                                               |


5. Click **OK.** The adapter now appears in the list of adapters in the right window of the BizTalk Administration console.  

#### Create a Receive Port and Location that uses the Adapter  

1. Expand the **BizTalk Group[server name]** node in [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **Applications** node, expand **BizTalk Application 1** node.  

2. Right-click **Receive Ports**, and then click **New**, select **One-Way Receive Port.**  

3. For **Name**, enter **TxnReceivePort1**, and then click **OK**.  

4. Right-click the **Receive Locations** node, click **New**, and then select **One-Way Receive Location**.  

5. In the**Select a Receive Port** dialog box, select **TxnReceivePort1**, and then click **OK**.  

6. In the **Receive Location Properties** dialog box, under the **General** tab, enter **TxnReceiveLocation1** for **Name**. Ensure the **Receive Port** label displays **TxnReceivePort1**.  

7. In the**Type** dropdown list box, in the **Transport** frame, select **TransactionalAdapter.**  

8. In the **Receive**<strong>Pipeline</strong> box, ensure **PassThruReceive** is selected. Leave the rest of the properties with their default settings.  

9. Click the **Configure** button next to the **Type** drop down box. This displays a dialog specific to this adapter. Specify the following as you see appropriate, then click **OK**.  


   |       Property        |                                                                           Setting                                                                            |
   |-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   Connection String   | The SQL database connection string used to connect and authenticate with the Northwind database. We will later run a SQL script that will use this database. |
   |     Command Text      |                      The SQL statements that are executed against the Northwind database to obtain data to put into a BizTalk Message.                       |
   |        Cookie         |               Comprises part of the URI so enter a unique value, such as the name of the receive location, for instance: TxnReceiveLocation1.                |
   | Polling Interval Unit |                                    The number of units of time measure for the polling of the data. Set this to seconds.                                     |
   |   Polling Interval    |                                        The unit of time measure for the polling of the data. Set this to 15 seconds.                                         |


10. Click **OK** to close the Configure dialog box, then **OK** again to close the **Receive Location Properties** dialog box to return to the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  

#### Create a Send Port and Send Handler that use the Adapter  

1.  With the **BizTalk Application 1** node still expanded, right-click **Send Ports**, and then click **New**, and select **Static One-Way Send Port**.  

2.  In the **Name** field, enter **TxnSendPort1**.  

3.  In the **Transport** frame, in the **Type** drop-down list, select**TransactionalAdapter**`.`  

4.  In the **Send Pipeline** box, ensure **PassThruTransmit** is selected.  

5.  Click the **Configure** button next to the **transport** drop-down list.In the dialog that appears specify the following as you see appropriate, then click **OK**.  

    |Property|Setting|  
    |--------------|-------------|  
    |Cookie|Comprises part of the URI - Enter a unique value here such as the name of the receive location, for instance: **TxnSendPort1**.|  
    |Connection String|The SQL database connection string used to connect and authenticate with the Northwind database. It will most likely be the same one used to configure the **TxnReceiveLocation1** receive location.|  
    |Stored Procedure|The stored procedure name that gets executed to poll the database - **sp_txnProc**. The body of the BizTalk message is given to that stored procedure as a string parameter called @Data. For example, the user will in this case later configure the stored procedure with the name **sp_txnProc**. The runtime of the adapter would execute the equivalent of this call to the database.<br /><br /> exec sp_txnProc @Data = “the contents of the BizTalk message”|  

6.  In the left navigation pane, click **Filter**.  

7.  In the filter expression editor, enter the following expression to set up a subscription for this send port to receive any messages received by the TxnReceivePort1 receive port.  

     Enter these values:**BTS.ReceivePortName== TxnReceivePort1**  

    1.  `(property)`  **BTS.ReceivePortName**  

    2.  `(operator)`  **==**  

    3.  `(value)`  **TxnReceivePort1**  

8.  Use the default values for the remainder of the adapter properties and select **OK**.  

## Run the sample  

1. Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, select **SQL Server Management Studio**.  

2. In the **Connect to Server** dialog box, make sure **Server Type** is set to **Database Engine**, and enter credentials to authenticate to the database server, then select **Connect**.  

3. Select the **New Query** toolbar button and paste the following into the new query window to insert a test table, test data, and a test stored procedure into the Northwind database. Select the **Execute** toolbar button.  

   ```  
   use [Northwind]  
   GO  
   if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[scratch]') and OBJECTPROPERTY(id, N'IsUserTable') = 1)  
   drop table [dbo].[scratch]  
   GO  
   CREATE TABLE [dbo].[scratch] (  
        [id] [int] IDENTITY (1, 1) NOT NULL ,  
        [msg] [nvarchar] (4000) NOT NULL   
   ) ON [PRIMARY]  
   GO  
   GRANT SELECT , UPDATE , INSERT ON [dbo].[scratch] TO [public]  
   GO  
   if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_txnProc]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
   drop procedure [dbo].[sp_txnProc]  
   GO  
   CREATE PROCEDURE [dbo].[sp_txnProc] @Data nvarchar (4000)  
   AS   
   INSERT scratch ( msg ) values ( @Data )  
   GO  
   GRANT EXECUTE ON [dbo].[sp_txnProc] TO [public]  
   GO  
   ```  

4. In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **Send Ports** node, select the **TxnSendPort1** send port, and select **Start**.  

5. In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **ReceiveLocations** node, select the **TxnRecieveLocation1** receive location, and then select **Enable**.  

6. Once the receive location is enabled, it will automatically poll the database at the designated intervals for data.  

## Classes or Methods Used in the sample  
* IBTTransmitterBatch Interface (COM)

* IBTTransportProxy Interface (COM)

These methods are described [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 

## See Also  
 [Adapter Samples - Development](../core/adapter-samples-development.md)   
 [Registering an Adapter](../core/registering-an-adapter.md)