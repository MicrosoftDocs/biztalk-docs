---
title: "Configure the binding properties for Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "binding properties, specifying at run time"
  - "binding properties, specifying at design time"
ms.assetid: c59a1b5c-b52b-4161-82de-c4d89bfce5c7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the binding properties for Oracle Database
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces several binding properties that enable you to control some of its behavioral characteristics. This section provides information about setting the binding properties from Visual Studio and from the BizTalk Server Administration console. From Visual Studio, you must specify the binding properties while generating schema for specific operations. From BizTalk Server, you must specify the binding properties as part of the send or receive port for sending or receiving messages from the Oracle database.  

 For information about the binding properties, including a list of binding properties for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  

## Specifying Binding Properties from Visual Studio  
 From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To specify binding properties using Consume Adapter Service Add-in  

1.  Right-click your BizTalk project and then select **Add Generated Items**.  

2.  In the **Add Generated Items** dialog box, do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Categories**|Click **Consume Adapter Service**.|  
    |**Templates**|Click **Consume Adapter Service**.|  

3.  To start the **Consume Adapter Service** dialog box, click **Add**.  

4.  In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **oracleDBBinding**, and click **Configure**.  

5.  In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the different binding properties.  

6.  Click **OK**.  

#### To specify binding properties using Add Adapter Metadata Wizard  

1. Right-click your BizTalk project and then select **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |           To do this            |
   |----------------|---------------------------------|
   | **Categories** |     Click **Add Adapter**.      |
   | **Templates**  | Click **Add Adapter Metadata**. |


3. Click **Add**. The Add Adapter Metadata Wizard opens.  

4. In the Add Adapter Metadata Wizard, select **WCF-OracleDB**. Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.  

   > [!IMPORTANT]
   >  If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.  

5. Click **Next**.  

6. In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **oracleDBBinding**, and click **Configure**.  

7. In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema. For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  

   > [!NOTE]
   >  If you selected an existing WCF-OracleDB send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such a case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  

8. Click **OK**.  

## Specifying Binding Properties from the BizTalk Server Administration Console  
 From the BizTalk Server Administration console, you must specify the binding properties as part of the WCF-Custom or WCF-OracleDB port configuration.  

#### To specify binding properties for the WCF-Custom port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

4. In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.  

5. From the **Binding Type** drop-down list, select **oracleDBBinding**.  

6. In the **Configuration** box, specify the values for the different binding properties and click **OK**.  

#### To specify binding properties for the WCF-OracleDB port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. Add the WCF-OracleDB adapter to the BizTalk Server Administration console. For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  

3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleDB adapter you added earlier, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

5. In the transport properties dialog box, click the **Binding** tab, and specify values for binding properties.  

   > [!NOTE]
   >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.  

## See Also  
[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)