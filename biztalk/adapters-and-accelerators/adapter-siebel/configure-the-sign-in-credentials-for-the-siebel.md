---
title: "Configure the sign in credentials for the Siebel | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "how to, specify credentials for the Siebel system at run time"
  - "credentials, specifying"
  - "how to, specify credentials for the Siebel system at design time"
ms.assetid: a9fef2ba-c38e-44f7-84a3-b6a95d4dc210
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the sign in credentials for the Siebel
The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] requires the adapter clients to provide client credentials. The adapter uses these credentials to authenticate the user with the Siebel system and to establish a connection.  

 Adapter clients can provide the client credentials either at design time or run time. At design time, credentials are required to generate the metadata. At run time, credentials are required to perform operations on the Siebel system. This section provides information about specifying client credentials at design time and run time.  

## Enter the client credentials at design time  
 For design time, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### Enter client credentials using Consume Adapter Service Add-in  

1.  Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.  

2.  In the **Add Generated Items** dialog box, do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Categories**|Click **Consume Adapter Service**.|  
    |**Templates**|Click **Consume Adapter Service**.|  

3.  To start the **Consume Adapter Service** dialog box, click **Add**.  

4.  In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **siebelBinding**, and then click **Configure**.  

5.  In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.  

6.  Click **OK**.  

#### Enter client credentials using Add Adapter Metadata Wizard  

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

6. In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **siebelBinding**, and then click **Configure**.  

7. In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.  

8. Click **OK**.  

## Enter client credentials at run time  
 For run time, you must specify the client credentials as part of the WCF-Custom or WCF-Siebel port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

#### Enter credentials for the WCF-Custom port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  

3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  

4. For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.  

   -   Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.  

5. Click **OK**.  

> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] also supports the Enterprise Single Sign-On (ESSO) system. ESSO is only applicable in the BizTalk scenario, in which the WCF adapter is aware of ESSO affiliate applications. For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).

#### Enter credentials for the WCF-Siebel port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  

3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  

4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-Siebel port you added earlier, and then click **Configure**.  

5. For a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.  

   -   Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.  

6. Click **OK**.  

> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] also supports the Enterprise Single Sign-On (ESSO) system. ESSO is only applicable in the BizTalk scenario, in which the WCF adapter is aware of ESSO affiliate applications. For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).

## See Also  
[Building blocks to create BizTalk applications with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)