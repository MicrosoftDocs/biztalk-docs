---
description: "Learn more about: Fragmented Inbound Batch"
title: "Fragmented Inbound Batch"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
---
# Fragmented Inbound Batch
You can configure [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to receive a message batch, extract the messages from the batch, and then route the individual messages to the destination system. If you enable fragmentation, the inbound batch fragments into individual messages; otherwise, the batch is processed and routed as a single 'batch' or interchange. You use BTAHL7 Configuration Explorer to enable batching. For more information about enabling batching, see [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).  
  
 The following describes a typical fragmented inbound batch scenario:  
  
1.  A line-of-business application, running on System A, sends a message batch to BTAHL7.  
  
     Batch messages can be in two different formats. BTAHL7 can process the following formats:  
  
    -   Format 1: Includes one file header and trailer (FHS/FTS) pair and one or more batch header and trailers (BHS/BTS).  
  
        ```  
        FHS  
        BHS  
        MSH  
        .............  
        MSH  
        ...........  
        BTS  
        BHS  
        MSH  
        ..............  
        MSH  
        ...............  
        BTS  
        FTS  
        ```  
  
    -   Format 2: Does not contain HL7 defined file and batch wrappers, and suspends a series are messages in a stream.  
  
        ```  
        MSH  
        .......  
        MSH  
        ........  
        MSH  
        .........  
        ```  
  
2.  BTAHL7 creates individual messages from the batch and then verifies the individual messages against the appropriate schemas.  
  
3.  BTAHL7 sends a separate acknowledgment message to System A for each message extracted from the batch.  
  
4.  BTAHL7 routes the individual messages to the destination system based on the routing information in the individual messages, rather than the message batch header.  
  
    > [!NOTE]
    >  BTAHL7 does not validate batch and file headers/trailers when the **FHS3** field (sending party) contains a trading partner that has fragmentation enabled.  
  
## See Also  
 [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)
