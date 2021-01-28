---
description: "Learn more about: Preparing to Use the Tutorial"
title: "Preparing to Use the Tutorial1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4a792b2-8351-4ae8-9d7c-75420c00af03
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preparing to Use the Tutorial
You must do the following before using the A4SWIFT adapter end-to-end tutorial.

1.  You will need the following SWIFT artifacts for this tutorial:

    -   SWIFT Alliance Gateway (SAG) 6.1

    -   Remote Access (RA) 6.1

    -   SWIFT WebStation 6.0

    -   SWIFTNet Link (SNL) 6.1

2.  You must configure SAG: create the MessagePartners, End Points, and Routing Rules in SAG, and test SAG connectivity on the computer where you install the adapters. For information, see the SAG documentation.

3.  Follow the instructions listed in the topic “How to Create a New Host” in Microsoft BizTalk Server Help ([https://go.microsoft.com/fwlink/?LinkId=100422](https://go.microsoft.com/fwlink/?LinkId=100422)) to create one in-process Host for the InterAct adapter, named *interacthost*, and one in-process Host for the FileAct adapter, named *fileacthost*. You will use these hosts while creating handlers for the adapters.

4.  Create the following folders for the tutorial:

    -   c:\SWIFTAdapterTutorial\Fileact\ClientLocation

    -   c:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime

    -   c:\SWIFTAdapterTutorial\Fileact\ResponseClient

    -   c:\SWIFTAdapterTutorial\Fileact\ResponseServer

    -   c:\SWIFTAdapterTutorial\Fileact\ServerLocation

    -   c:\SWIFTAdapterTutorial\Fileact\StatusEvents

    -   c:\SWIFTAdapterTutorial\Fileact\PullRequest

    -   c:\SWIFTAdapterTutorial\Fileact\PullResponse

    -   c:\SWIFTAdapterTutorial\Interact\HandleRequest

    -   c:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime

    -   c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF

    -   c:\SWIFTAdapterTutorial\Interact\Response

    -   c:\SWIFTAdapterTutorial\Interact\PullRequest

    -   c:\SWIFTAdapterTutorial\Interact\Pullresponse

5.  You must have a connection to SWIFT ITB or live environment to test the adapter.

## See Also
 [BizTalk FileAct and InterAct Adapters End-to-End Tutorial](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md)
 [InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)
 [InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)
 [FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)
 [FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)
