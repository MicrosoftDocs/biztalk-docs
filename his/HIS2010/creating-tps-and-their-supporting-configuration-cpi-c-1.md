---
title: "Creating TPs and Their Supporting Configuration (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: faa9a862-b89a-4688-a80a-93dec8a26800
caps.latest.revision: 3
---
# Creating TPs and Their Supporting Configuration (CPI-C)
The following procedure describes how to create transaction programs (TPs) and set up a supporting configuration.  
  
#### To create TPs and set up a supporting configuration  
  
1.  Write, compile, and link each TP.  
  
2.  Place each TP on an appropriate computer.  
  
     For TPs that you start many times or that are started by a user, arrange for the TP to be started easily. That is, for graphical interfaces, create a program icon for starting the TP and for non-graphical interfaces, make sure the TP is in the path.  
  
3.  On one or more computers running Host Integration Server, configure logical units (LUs), modes, LU-LU pairs, and a symbolic destination name for use by the TPs.  
  
     For information about how to set up LU-LU pairs to support TPs, see [Using Invoking and Invokable TPs](../HIS2010/invoking-and-working-with-invokable-tps-cpi-c-2.md).  
  
     For information about symbolic destination names and side information, see [Side Information for CPI-C Programs](../HIS2010/side-information-for-cpi-c-programs2.md).  
  
4.  Set any registry or environment variables needed for the invoking and invokable TPs.  
  
     For autostarted invokable TPs, it is recommended that you use the sample TP configuration program, TPSETUP, for this step. When you write an installation program for autostarted invokable TPs, it is recommended that you include code similar to TPSETUP.  
  
     For information about registry or environment variables, see [Configuring Invokable TPs](../HIS2010/configuring-invokable-tps-cpi-c-2.md) and [Invoking TPs](../HIS2010/invoking-tps-cpi-c-1.md). For information about TPSETUP, see [CPI-C Samples](../HIS2010/cpi-c-samples.md).  
  
5.  If the invokable TP is operator-started, start it, or arrange for it to be started when the computer is restarted, and then restart the computer.  
  
     If the invokable TP is autostarted, Host Integration Server will start it when needed.  
  
6.  Start the invoking TP.