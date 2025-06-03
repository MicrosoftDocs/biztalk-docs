---
description: "Learn more about: Create TPs and Their Supporting Configuration"
title: "Create TPs and Their Supporting Configuration"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Create TPs and Their Supporting Configuration
The following procedure describes how to create transaction programs (TPs) and set up a supporting configuration.  
  
1.  Write, compile, and link each TP.  
  
2.  Place each TP on an appropriate computer.  
  
     For TPs that you start many times or that are started by a user, arrange for the TP to be started easily. That is, for graphical interfaces, create a program icon for starting the TP; for non-graphical interfaces, make sure the TP is in the path.  
  
3.  On one or more servers running Host Integration Server, configure logical units (LUs), modes, and LU-LU pairs for use by the TPs.  
  
     For information about how to set up LU-LU pairs to support TPs, see [Using Invoking and Invokable TPs](../core/invoking-and-invokable-tps1.md).  
  
4.  Set any registry or environment variables needed for the invokable TP.  
  
     For autostarted invokable TPs, it is recommended that you use the sample TP configuration program, TPSETUP, for this step. When you write an installation program for autostarted invokable TPs, it is recommended that you include code similar to TPSETUP.  
  
     For information about registry or environment variables, see [Configuring Invokable TPs](../core/configuring-invokable-tps1.md). 
  
5.  If the invokable TP is operator-started, start it, or arrange for it to be started when the computer is restarted and then restart the computer.  
  
     If the invokable TP is autostarted, Host Integration Server will start it when needed.  
  
6.  Start the invoking TP.
