---
title: "Step 13: Create and Configure Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ports, creating"
  - "message enrichment tutorial, ports"
  - "creating, ports"
  - "configuring, ports"
  - "ports, configuring"
ms.assetid: cc0540d7-46fc-4d9f-bcf3-0b0e0179fd51
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 13: Create and Configure Ports
In this step, you use the Port Configuration Wizard to create and configure ports in Orchestration Designer. Ports specify how your orchestration sends and receives messages to and from business processes. Each port has a type, a direction, and a binding. The properties together determine the direction of communication, the pattern of communication, the location to or from which [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] sends or receives the message, and how the communication takes place. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses the Minimum Lower Layer Protocol (MLLP) adapter as a send port. The MLLP adapter uses TCP sockets communication to interface with other applications, such as laboratory applications, insurance applications, and legacy line-of-business applications. The MLLP Send Adapter represents a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter that is:  

- Customized. The adapter only ships with [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], as opposed to shipping with BizTalk Server.  

- Protocol/Transport. The adapter is not an application or data adapter.  

- Static. The adapter configuration does not involve a custom user interface.  

- Asynchronous. The adapter does not block the Messaging Engine thread, which enables increased performance of all adapters that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hosts.  

- Nontransacted. The adapter is not a transacted receive or send [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter.  

- Regular. The adapter does not run in a separate application process.  

- Both One-Way and Two-Way. The adapter supports both One-way and Request-Response/Solicit-Response modes of interaction.  

  The MLLP adapter can submit individual messages or submit messages in a batch. The beginning of an MLLP message is marked with a wrapper character, hexadecimal 0x0b (also known as the Start Block or SB character), and the end of the message is marked by the combination of a hexadecimal 0x1c character (also known as the End Block or EB character) immediately followed by the 0x0d character (Carriage Return). BTAHL7 performance counters only count these wrapper characters for sent messages. BTAHL7 performance counters do not count these wrapper characters when receiving messages.  

> [!NOTE]
>  The MLLP protocol standard does not allow characters under 0x20 in the message payload because it interferes with the ability to detect the SB and EB characters. You can configure the SB and EB character values, so be wary of this issue when making changes.  

 In this step, you configure the MLLP adapter and SOAP adapter.  

### To create and configure the ports  

1. In Orchestration Designer, drag the **Port** shape from the Toolbox to the Port Surface on the left side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellReceive** shape.  

2. In the **Port Configuration Wizard**, click **Next**.  

3. On the **Port Properties** page, in the **Name** field, type **SOAPReceivePort**, and then click **Next**.  

4. On the **Select a Port Type** page, enter the following information, and then click **Next** to continue.  


   |         Use this          |          To do this           |
   |---------------------------|-------------------------------|
   |    **Port Type Name**     | Type **SOAPReceivePortType**. |
   | **Communication Pattern** |      Select **One-Way**.      |
   |  **Access Restrictions**  | Select **Public - no limit**. |


5. On the **Port Binding** page, click **Next** to accept the default values.  

6. On the **Completing the Port Wizard** page, click **Finish**.  

7. Drag the **Port** shape from the Toolbox to the Port Surface on the right side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellSend** shape.  

8. Using the **Port Configuration Wizard** as you did in steps 2 through 7, create an additional send port using the following parameters:  


   |              Property               |                   Parameter                   |
   |-------------------------------------|-----------------------------------------------|
   |      **Port Properties Name**       |                 MLLPSendPort                  |
   |         **Port Type Name**          |               MLLPSendPortType                |
   |      **Communication Pattern**      |                    One-Way                    |
   |       **Access Restrictions**       |               Public - no limit               |
   |          **Port Binding**           |                 Specify Later                 |
   | **Port direction of communication** | I'll always be sending messages on this port. |


9. In the **Orchestration View** window, with the **Types**, **Ports Types**, and **SOAPReceivePortType** nodes expanded, expand **Operation_1**, and then click **Request**.  

10. In the **Properties** window, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7_Project.Doorbell**.  

11. In the **Orchestration View** window, expand **MLLPSendPortType**, expand **Operation_1**, and then click **Request**.  

12. In the **Properties** window, in the drop-down list for **Message Type**, expand **Multi-part Message Types**, and then click **BTAHL7_Project.DoorbellFinalMessageType**.  

13. In the **Name** field, type **Response**, then press **Enter**.  

14. On the orchestration Design view surface, click the **DoorbellReceive** action shape.  

15. In the **Properties** window, in the drop-down list for **Message**, select **DoorbellInputMessage**.  

16. On the orchestration Design view surface, click the **DoorbellSend** shape.  

17. In the **Properties** window, in the drop-down list for **Message**, select **DoorbellFinalMessage**.  

18. Click the green handle in the **SOAPReceivePort** and drag it to the green handle on the **DoorbellReceive** receive shape to connect the **SOAPReceivePort** to the **DoorbellReceive** receive shape.  

19. Click the green handle in the **DoorbellSend** shape and drag it to the green handle on the **MLLPSendPort** port to connect the **DoorbellSend** send shape to the **MLLPSendPort** port.  

20. Click the **Solution Explorer** tab under the Orchestration View.  

21. In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Build**. Ensure that a success message appears in the output window.  

    > [!NOTE]
    >  If no success message appears, troubleshoot the solution.  

22. Right-click **BTAHL7 Project**, and click **Deploy** to deploy the BTAHL7 project.  

    Proceed to [Step 14: Publish the Orchestration as a Web Service](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md).  

## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)