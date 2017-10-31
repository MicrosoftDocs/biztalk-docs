---
title: "Creating TPs and Their Supporting Configuration2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 761365be-10a0-4237-b3a4-b4a91425f1d9
caps.latest.revision: 3
---
# Creating TPs and Their Supporting Configuration
The following procedure describes how to create transaction programs (TPs) and set up a supporting configuration.  
  
### To create TPs and set up a supporting configuration  
  
1.  Write, compile, and link each TP.  
  
2.  Place each TP on an appropriate computer.  
  
     For TPs that you start many times or that are started by a user, arrange for the TP to be started easily. That is, for graphical interfaces, create a program icon for starting the TP; for non-graphical interfaces, make sure the TP is in the path.  
  
3.  On one or more servers running Host Integration Server, configure logical units (LUs), modes, and LU-LU pairs for use by the TPs.  
  
     For information about how to set up LU-LU pairs to support TPs, see [Using Invoking and Invokable TPs](../core/invoking-and-invokable-tps.md).  
  
4.  Set any registry or environment variables needed for the invokable TP.  
  
     For autostarted invokable TPs, it is recommended that you use the sample TP configuration program, TPSETUP, for this step. When you write an installation program for autostarted invokable TPs, it is recommended that you include code similar to TPSETUP.  
  
     For information about registry or environment variables, see [Configuring Invokable TPs](../core/configuring-invokable-tps.md). For information about TPSETUP, see [APPC Samples](../Topic/APPC%20Samples.md).  
  
5.  If the invokable TP is operator-started, start it, or arrange for it to be started when the computer is restarted and then restart the computer.  
  
     If the invokable TP is autostarted, [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] will start it when needed.  
  
6.  Start the invoking TP.