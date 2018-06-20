---
title: "Connecting to SAP in Visual Studio Using Add Adapter Metadata Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a442837b-e7d8-4edb-9c5e-5603d4c58fe5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connecting to SAP in Visual Studio Using Add Adapter Metadata Wizard
The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is also exposed as a BizTalk adapter and hence, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on an SAP system using the adapter.  

## Connecting to an SAP System Using Add Adapter Metadata Wizard  
 Perform the following steps to connect to an SAP system using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To connect to an SAP system  

1. To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:  

   1. Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

   2. Right-click the project name in Solution Explorer, point to **Add**, and then click **Add Generated Items**.  

   3. In the **Add Generated Items** dialog box, do the following:  


      |    Use this    |           To do this            |
      |----------------|---------------------------------|
      | **Categories** |     Click **Add Adapter**.      |
      | **Templates**  | Click **Add Adapter Metadata**. |


   4. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

   5. In the Add Adapter Wizard, select **WCF-SAP**. Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.  

      > [!IMPORTANT]
      >  If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.  

   6. Click **Next**.  

2. From the **Select a binding** drop-down list, select **sapBinding** and click **Configure**.  

3. In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.  

   > [!IMPORTANT]
   >  If you are using the SAP Secure Network Connection (SNC) library to connect to an SAP system, do not specify a username and password.  

4. Click the **URI Properties** tab and specify values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  

   > [!IMPORTANT]
   >  If you are using the SAP SNC library to connect to an SAP system, set the **UseSnc** connection property to **True**.  

   > [!NOTE]
   >  If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

5. Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target. For example, if you want to target a ReceiveIdoc operation you must set the **ReceiveIdocFormat** binding property to String. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  

   > [!NOTE]
   >  If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-SAP send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  
   > 
   > [!IMPORTANT]
   >  If you are using the SAP SNC library to connect to an SAP system, set the **SncLibrary** and **SncPartnerName** to appropriate values.  
   > 
   >  The **SncLibrary** binding property takes the path and the filename of the DLLs required for using SNC to connect to an SAP system. These DLLs must be present on the computer with the SAP client and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] installed. For more information see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide available at \<installation guide\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.  
   > 
   >  The **SncPartnerName** binding property takes the SNC name of the communication partner.  

6. Click **OK**.  

7. Click **Connect**. After the connection is established, the connection status is shown as **Connected**.  

    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established. The graphical user interface is same for the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

    ![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-sap/media/00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0.gif "00eb7c9c-3af3-4dad-8c97-2e6ae211b8f0")  

    The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various artifacts that can be invoked in an SAP system. For example, the **RFC** node contains all the RFCs available in the SAP system you connected to. For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  

## See Also  
 [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)