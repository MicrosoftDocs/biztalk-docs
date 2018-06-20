---
title: "Configure the connection URI for the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection URI, specifying at run time"
  - "connection URI, specifying at design time"
ms.assetid: 8df8e4a7-13f7-48c0-8af2-451253ced7e7
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the connection URI for the SAP adapter
A connection URI is a connection string to connect to an SAP system. It contains various parameters required to establish connection with an SAP system. At design time, you must specify the URI to connect to the SAP system to generate the metadata. At run time, you must specify the URI to connect to the SAP system to perform operations.  

## Enter the connection URI at design time  
 For design time, you can specify the connection URI using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

### Enter the connection URI using Consume Adapter Service Add-in  

1. Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |             To do this             |
   |----------------|------------------------------------|
   | **Categories** | Click **Consume Adapter Service**. |
   | **Templates**  | Click **Consume Adapter Service**. |


3. To start the **Consume Adapter Service** dialog box, click **Add**.  

4. In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.  

5. In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list boxes, select **Username** and specify the user name and password to connect to the SAP system.  

6. Click the **URI Properties** tab and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  

7. Click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema. For example, you must specify a value for the **GenerateFlatFileCompatibleIDoc** property before generating schema for receiving IDOC from an SAP system. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  

8. Click **OK**.  

### Enter the connection URI using Add Adapter Metadata Wizard  

1. Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |           To do this            |
   |----------------|---------------------------------|
   | **Categories** |     Click **Add Adapter**.      |
   | **Templates**  | Click **Add Adapter Metadata**. |


3. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

4. In the Add Adapter Wizard, select **WCF-SAP**. Select the computer on which BizTalk Server is installed and the name of the BizTalk database.  

   > [!IMPORTANT]
   >  If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.  

5. Click **Next**.  

6. In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **sapBinding**, and click **Configure**.  

7. In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list boxes, select **Username** and specify the user name and password to connect to the SAP system.  

8. Click the **URI Properties** tab and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  

9. Click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema. For example, you must specify a value for the **GenerateFlatFileCompatibleIDoc** property before generating schema for receiving IDOC from an SAP system. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  

    > [!NOTE]
    >  If you selected an existing WCF-SAP send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  

10. Click **OK**.  

## Enter the connection URI at run time  
 For run time, you can specify the URI as part of the WCF-Custom or WCF-SAP port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

### Enter the connection URI for the WCF-Custom port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

4. In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.  

5. In the **Address (URI)** text box, specify the connection URI to connect to the SAP system. For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  

6. In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **sapBinding**.  

7. If you are creating a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:  

   1.  Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the SAP system.  

   2.  Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

8. If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:  

   1.  Select **User account** option, and specify the user name and password to connect to the SAP system.  

   2.  Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  

9. Click **OK**.  

### Enter the connection URI for the WCF-SAP port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  

3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

5. In the transport properties dialog box, click the **General** tab.  

6. Click the **Configure** button and provide values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  

7. In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.  

   > [!NOTE]
   >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.  

8. If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:  

   1.  Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the SAP system.  

   2.  Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

9. If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:  

    1.  Select **User account** option, and specify the user name and password to connect to the SAP system.  

    2.  Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  

10. Click **OK**.  

## See Also  
[Building blocks to create SAP applications](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)