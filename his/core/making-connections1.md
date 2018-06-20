---
title: "Making Connections1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c02e13e-8ab7-42d5-81d6-0f935fb3a761
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Making Connections
Before messages can flow across a connection, the connection must be established or opened. This is necessary because a partner (P1) does not initially know the locality partner index (LPI) address of the partner with which it wants to communicate. There may not even be a suitable partner with which to communicate.  
  
 A component of the Base, known as the Resource Locator, and a message with a type of Open, known as an Open message, are used to establish a connection between partners.  
  
 The following procedure outlines how a connection is established. More specific information is available in [Function Management Interface](../core/function-management-interface2.md).  
  
### To establish a connection between partners  
  
1. The Open message has two forms: an Open request and an Open response. The Open request contains information on the type of partner P1 is looking for.  
  
    P1 fills in an Open request and calls the Base with it. Because it does not know the LPI address of its partner, it sets the destination LPI values to zero.  
  
2. The Base cannot forward the Open to a particular partner, because it has no destination LPI address. Therefore it passes the Open to the Resource Locator, which attempts to find a locality that will accept the Open. The Dynamic Access Module (DMOD) has a record of all the localities that could accept this type of Open. The Resource Locator tries each of these localities until the Open is accepted. If no locality is found, the Resource Locator returns a negative response to the Open to inform the sender that no partner could be found.  
  
3. When a remote locality receives an Open, the Base passes the Open to the partner (P2). If P2 can accept the Open, it responds by sending a positive Open response message to P1.  
  
4. The Open response message returned to P1 contains both the source and destination LPI values for the particular connection. At the end of this exchange, both P1 and P2 know each other's addresses and can communicate over the connection.  
  
   The terms source and destination in the context of LPIs refer to the source and destination of the particular message. When the 3270 emulator builds a message to send to the local 2.1 node, it needs to swap the source and destination LPIs received on the Open response from the local 2.1 node.  
  
   For a detailed example of how LPI addresses are assigned during initialization of the system services control point (SSCP) and primary logical unit (PLU) sessions, see [Opening the PLU Connection](../core/opening-the-plu-connection1.md).