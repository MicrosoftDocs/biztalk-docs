---
title: "Step 5: Create the Receive Port for Accepting HIS Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interrogative tutorial, receive ports"
ms.assetid: c0b311d8-541c-4c21-a514-c93092c36fe2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Create the Receive Port for Accepting HIS Messages
In this step you create a receive port to specify the location for incoming messages sent by the Hospital Information System (HIS). Use the following procedure to create the receive port for accepting query response messages from the ADT system using the Minimal Lower Layer Protocol (MLLP) adapter.  

## Create the HIS_ReceivePort receive port  

1. Open **BizTalk Server Administration**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  

2. Right-click **Receive Ports**, select **New**, and then select **One-way Receive Port**.   

3. For the **Name**, enter **HIS_ReceivePort**.  

4. Select **Apply** to bind the port, and then select **Receive Locations**.  

5. Select **New**.  

6. For the **Name**, enter **HIS_Receive**.  

7. In the **Transport** section, select **Type**, and then select **MLLP** from the drop-down list.  

8. Select **Configure**. In **MLLP Transport Properties**, configure the following, and then select **OK**.  


   |           Use this           |                                                                                                                                                                                                     To do this                                                                                                                                                                                                     |
   |------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Connect retry time (sec)** |                                                                 New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>The upper limit of time to wait before attempting to reconnect a dropped or closed connection. Applicable when **Connection Initiated by** is set to **Local**.<br/><br/>Default is 20 seconds.                                                                  |
   | **Connection initiated by**  | New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter **Local** for the MLLP receive location to initiate the connection to a remote LOB server. This is the new option.<br/><br/>Enter **Remote** for the MLLP receive location to continue to listen for a connection from the remote LOB server. This is the backwards-compatible default option.<br/><br/>Default is Remote. |
   |     **Connection Name**      |                                                                                                                                                                                             Enter **HIS_ReceiveMLLP**.                                                                                                                                                                                             |
   |        **Host name**         |                                                                                                                                              Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions. <br/><br/>Enter **localhost**.                                                                                                                                               |
   |     **Local Host name**      |                                                                            New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the DNS name or IP address of the local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. You can also enter **localhost**.                                                                             |
   |           **Port**           |                                                                                                                                                Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions. <br/><br/>Set to **23000**.                                                                                                                                                |
   |        **Local Port**        |                                                                                       New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the TCP port number for the LocalHost connection. Applicable only when **Connection Initiated by** is **Remote**. <br/><br/>Set to **23000**.                                                                                        |
   |       **Remote Host**        |                                                                                                   New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the DNS name or IP address of the remote LOB server. Applicable when **Connection Initiated by** is set to **Local**.                                                                                                    |
   |       **Remote Port**        |                                                                                      New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Enter the TCP port number for the remote host connection. Applicable when **Connection Initiated by** is set to **Local**.<br/><br/>Set to **23000**.                                                                                       |


9. Set the **Receive Handler** to **BizTalkServerApplication**.  

10. Set the **Receive Pipeline** to **BTAHL72XPipelines.BTAHL72XReceivePipeline**.  

11. Select **OK** to save your changes.  

12. Enable the receive location you just created by right-clicking it, and then select **Enable**.  

## Next step  
[Step 6: Create a Send Port to Deliver Query Messages](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-query-messages.md)