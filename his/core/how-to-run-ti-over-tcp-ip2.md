---
description: "Learn more about: Run TI Over TCP/IP"
title: "Run TI Over TCP-IP2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Run TI Over TCP/IP

## Overview
You can install and run Transaction Integrator (TI) over TCP/IP without installing or using any of the SNA services of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
 Use the following procedure to run a TI application over TCP/IP.  
  
## Run a TI application over TCP/IP  
  
1. Configure the mainframe (CICS or IMS) for TCP/IP, and establish a connection with your Windows-based [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Server computer.  
  
    For more information, see the following:  
  
   -   [Configuring CICS for TCP/IP](../core/configuring-cics-for-tcp-ip2.md)  
  
   -   [Configuring IMS for TCP/IP](../core/configuring-ims-for-tcp-ip2.md).  
  
   -   [Enhanced Listener CICS Administration](./enhanced-listener-cics-administration2.md)  
  
2. Install the COBOL programs within the CICS or IMS region that receives TI-initiated calls.  
  
3. Define an appropriate TCP/IP remote environment for the CICS or IMS region that receives TI-initiated calls.  
  
4. Build the TI component with a method for each transaction in the transaction program (TP).  
  
5. Deploy the TI component in a COM+ application to create a TI Automation server.  
  
6. Run the client application that calls the new TI Automation server to automate the TP.  
  
## See Also  
 [Configuring CICS for TCP/IP](../core/configuring-cics-for-tcp-ip2.md)   
 [Configuring IMS for TCP/IP](../core/configuring-ims-for-tcp-ip2.md)   
 [Defining a TCP/IP Remote Environment](../core/defining-a-tcp-ip-remote-environment2.md)   
 [Windows-Initiated Processing Overview](../core/windows-initiated-processing-overview2.md)
