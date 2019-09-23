---
title: "How to Consume Web Service Arrays | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "SOAP adapters, Web services"
  - "Web services, arrays"
  - "orchestrations, Web services"
  - "orchestrations, Web ports"
ms.assetid: 29ecaaed-aa8a-4cf9-a7c8-4b0d6dd412ac
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Consume Web Service Arrays
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the ability to consume arrays that are exposed in Web services from a BizTalk Orchestration.

 **To configure an Orchestration to consume an array exposed in a Web service:**

 Determine the URL for the Web service that exposes arrays. This is typically an asmx Web page that lists the operations supported by the Web service. For example: http://localhost/ArrayWS/ArraySvc.asmx.

1.  Add a Web reference to this URL in the Visual Studio project that contains your orchestration:

    -   In the Solution Explorer, right-click **References**, and click **Add Service Reference**.

    -   In the **Add Service Reference** dialog box, click **Advanced**.

    -   In the **Service Reference Settings** dialog box, click **Add Web Reference** in the **Compatibility** section.

    -   In the **Add Web Reference** dialog box, enter the URL for the Web service into the **URL** text box and then click **Go**.

    -   Enter a name for the Web reference into the **Web reference name** text box and click the **Add Reference** button.

    -   The Web reference will appear under **Web References** in the Solution Explorer.

        > [!TIP]
        >  Once you have a Web reference added to the project, the **Add Web Reference** command is directly available when you right-click the project name or **References** or **Web References**.

2.  Add a Web port to your orchestration:

    -   Drag a **Port** shape from the toolbox to one of the port surfaces in the Orchestration Designer to launch the **Port Configuration Wizard**. Click the **Next** button in the **Port Configuration Wizard** to display the **Port Properties** dialog.

    -   Enter a value into the **Name** text box to identify the port, and click the **Next** button to display the **Select a Port Type** dialog.

    -   Select the option to **Use an existing Port Type**, select the Web Port type that corresponds to the Web reference you added, and click the **Next** button to display the **Port Binding** dialog.

    -   In the **Port Binding** dialog select the appropriate **Port binding** option and click the **Next** button, then click the **Finish** button. You should now have a Web port displayed in the Orchestration Designer that includes the operations supported by the Web service.

3.  Add **Send** and **Receive** shapes to your Orchestration as appropriate:

    -   Drag a **Send** shape from the toolbox to a connecting line in the Orchestration Designer surface to configure the orchestration to send a request message to the Web port. If you connect the **Send** shape to one of the Web port request message connectors, BizTalk will automatically create a message of the appropriate type to be used when sending a request message to this port.

    -   Drag a **Receive** shape from the toolbox to a connecting line in the Orchestration Designer surface to configure the orchestration to receive a response message from the Web port. If you connect the **Receive** shape to one of the Web port response message connectors, BizTalk will automatically create a message of the appropriate type to be used when receiving a response message from this port.

> [!NOTE]
>  Use the SOAP Adapter to send messages to or receive messages from a Web service. For more information about configuring the SOAP Adapter see [Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md).

 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Orchestration Engine provides support for consuming both one dimensional and jagged arrays that are exposed by Web services. If you add a Web reference to a Web service that exposes arrays, the Orchestration Designer will generate a Web message type that describes the array. You can then send and receive messages of this type like any other message. BizTalk Server does not limit the sending of Web messages containing arrays to only Web ports.

 For an example of consuming Web service arrays, see the SDK sample "Consume Web Services" and "Consuming Web Services with Array Parameters" at [http://go.microsoft.com/fwlink/?LinkId=73703](https://go.microsoft.com/fwlink/?LinkId=73703).

## See Also
 [Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md)