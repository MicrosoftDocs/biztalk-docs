---
description: "Learn more about: Create TPs and Their Supporting Configuration (CPI-C)"
title: "Create TPs and Supporting Configuration (CPI-C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f788938-1776-4244-b91c-61ace533c26f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Create TPs and Their Supporting Configuration (CPI-C)
  
1.  Write, compile, and link each TP.  
  
2.  Place each TP on an appropriate computer.  
  
     For TPs that you start many times or that are started by a user, arrange for the TP to be started easily. That is, for graphical interfaces, create a program icon for starting the TP and for non-graphical interfaces, make sure the TP is in the path.  
  
3.  On one or more computers running Host Integration Server, configure logical units (LUs), modes, LU-LU pairs, and a symbolic destination name for use by the TPs.  
  
     For information about how to set up LU-LU pairs to support TPs, see [Using Invoking and Invokable TPs](../core/invoking-and-working-with-invokable-tps-cpi-c-1.md).  
  
     For information about symbolic destination names and side information, see [Side Information for CPI-C Programs](../core/side-information-for-cpi-c-programs1.md).  
  
4.  Set any registry or environment variables needed for the invoking and invokable TPs.  
  
     For autostarted invokable TPs, it is recommended that you use the sample TP configuration program, TPSETUP, for this step. When you write an installation program for autostarted invokable TPs, it is recommended that you include code similar to TPSETUP.  
  
     For information about registry or environment variables, see [Configuring Invokable TPs](../core/configuring-invokable-tps-cpi-c-1.md) and [Invoking TPs](../core/invoking-tps-cpi-c-2.md). 
  
5.  If the invokable TP is operator-started, start it, or arrange for it to be started when the computer is restarted, and then restart the computer.  
  
     If the invokable TP is autostarted, Host Integration Server will start it when needed.  
  
6.  Start the invoking TP.
