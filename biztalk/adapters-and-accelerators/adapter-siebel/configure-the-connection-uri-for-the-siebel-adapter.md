---
title: "Configure the connection URI for the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection URI, specifying"
ms.assetid: b89b60e9-0f3b-4305-865e-9d3b40d04648
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the connection URI for the Siebel adapter
A connection URI is a connection string to connect to a Siebel system. The connection URI contains various parameters required to establish connection with a Siebel system. You must specify this connection URI both at the design time and the run time. At design time, you must specify the URI to connect to the Siebel system to generate the metadata. At run time, you must specify the URI to connect to the Siebel system to perform operations.  

## Enter the connection URI at design time  
 For design time, you must specify the connection URI using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### Enter the connection URI using Consume Adapter Service Add-in  

1. Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |             To do this             |
   |----------------|------------------------------------|
   | **Categories** | Click **Consume Adapter Service**. |
   | **Templates**  | Click **Consume Adapter Service**. |


3. To start the **Consume Adapter Service** dialog box, click **Add**.  

4. In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **siebelBinding**, and click **Configure**.  

5. In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.  

6. In the **Configure Adapter** dialog box, click the **URI Properties** tab and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  

7. In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema. For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  

8. Click **OK**.  

#### Enter the connection URI using Add Adapter Metadata Wizard  

1. Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |           To do this            |
   |----------------|---------------------------------|
   | **Categories** |     Click **Add Adapter**.      |
   | **Templates**  | Click **Add Adapter Metadata**. |


3. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

4. In the Add Adapter Wizard, select **WCF-Siebel**. Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.  

   > [!IMPORTANT]
   >  If you already have a WCF-Siebel port configured in BizTalk, select the port from the **Port** list.  

5. Click **Next**.  

6. In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **siebelBinding**, and click **Configure**.  

7. In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.  

8. In the **Configure Adapter** dialog box, click the **URI Properties** tab and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  

9. In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the binding values, if any, which are required to be specified before generating the schema. For more information about binding properties, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  

    > [!NOTE]
    >  If you selected an existing WCF-Siebel send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  

10. Click **OK**.  

## Enter the connection URI at run time  
 For run time, you must specify the URI as part of the WCF-Custom or WCF-Siebel port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console.  

#### Enter the connection URI for the WCF-Custom port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and the click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  

3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  

4. In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.  

5. In the **Address (URI)** text box, specify the connection URI to connect to the Siebel system. For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  

6. In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **siebelBinding**.  

7. To create a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:  

   1.  Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.  

   2.  Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.  

8. Click **OK**.  

#### Enter the connection URI for the WCF-Siebel port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  

3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and the click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  

4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-Siebel adapter you added earlier, and then click **Configure**.  

5. In the transport properties dialog box, click the **General** tab.  

6. Click the **Configure** button and provide values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  

7. In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.  

8. To create a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:  

   1.  Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.  

   2.  Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.  

9. Click **OK**.  

## See Also  
[Building blocks to create BizTalk applications with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)