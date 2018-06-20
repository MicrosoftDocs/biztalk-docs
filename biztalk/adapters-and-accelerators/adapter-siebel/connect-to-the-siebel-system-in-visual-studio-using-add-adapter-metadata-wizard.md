---
title: "Connect to the Siebel System in Visual Studio Using Add Adapter Metadata Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0a82fcc-b3ac-4936-9210-03c99d3741d7
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to the Siebel System in Visual Studio Using Add Adapter Metadata Wizard
The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is also exposed as a BizTalk adapter and hence, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on the Siebel system using the adapter.  

## Connecting to a Siebel System Using Add Adapter Metadata Wizard  
 Perform the following steps to connect to a Siebel system using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To connect to a Siebel system  

1. To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:  

   1. Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

   2. Right-click the project in Solution Explorer, point to **Add**, and then click **Add Generated Items**.  

   3. In the **Add Generated Items** dialog box, do the following:  


      |    Use this    |             To do this             |
      |----------------|------------------------------------|
      | **Categories** | Click **Consume Adapter Service**. |
      | **Templates**  | Click **Consume Adapter Service**. |


   4. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

   5. In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select WCF-Siebel. Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.  

      > [!IMPORTANT]
      >  If you already have a **WCF-Siebel** port configured in BizTalk, select the port from the **Port** list.  

   6. Click **Next**.  

2. From the **Select a binding** drop-down list, select **siebelBinding**, and then click **Configure**.  

3. In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username**.  

4. Specify the user name and password to connect to the Siebel system.  

5. Click the **URI Properties** tab, and specify values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  

   > [!NOTE]
   >  If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

6. Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target. For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  

   > [!NOTE]
   >  If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-Siebel send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  

7. Click **OK**.  

8. Click **Connect**. Once the connection is established, the connection status is shown as **Connected**.  

    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.  

    ![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-01-connected.gif "SIEBEL-ADPT-Lesson1-Step3-01-connected")  

    The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various operations that can be performed on the Siebel system. For example, the **Business Objects** node contains all the business objects and business components that can be invoked on the Siebel system. Similarly, the **Business Services**  node contains all the business services in the Siebel system you connected to. For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).