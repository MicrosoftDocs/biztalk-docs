---
title: "How to Run TI Over TCP-IP1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff382659-5804-48ef-b343-0c12f4393f66
caps.latest.revision: 3
---
# How to Run TI Over TCP/IP
You can install and run Transaction Integrator (TI) over TCP/IP without installing or using any of the SNA services of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
 Use the following procedure to run a TI application over TCP/IP.  
  
### To run a TI application over TCP/IP  
  
1.  Configure the mainframe (CICS or IMS) for TCP/IP, and establish a connection with your Windows-based [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Server computer.  
  
     For more information, see the following:  
  
    -   [Configuring CICS for TCP/IP](../HIS2010/configuring-cics-for-tcp-ip1.md)  
  
    -   [Configuring IMS for TCP/IP](../HIS2010/configuring-ims-for-tcp-ip1.md).  
  
    -   [Configure Host Environment and Programming Model Wizard Page](../HIS2010/configure-host-environment-and-programming-model-wizard-page1.md) in the [New Remote Environment Wizard](../HIS2010/new-remote-environment-wizard2.md)  
  
    -   [Enhanced Listener CICS Administration](../HIS2010/enhanced-listener-cics-administration1.md)  
  
2.  Install the COBOL programs within the CICS or IMS region that receives TI-initiated calls.  
  
3.  Define an appropriate TCP/IP remote environment for the CICS or IMS region that receives TI-initiated calls.  
  
4.  Build the TI component with a method for each transaction in the transaction program (TP).  
  
5.  Deploy the TI component in a COM+ application to create a TI Automation server.  
  
6.  Run the client application that calls the new TI Automation server to automate the TP.  
  
## See Also  
 [Configuring CICS for TCP/IP](../HIS2010/configuring-cics-for-tcp-ip1.md)   
 [Configuring IMS for TCP/IP](../HIS2010/configuring-ims-for-tcp-ip1.md)   
 [Defining a TCP/IP Remote Environment](../HIS2010/defining-a-tcp-ip-remote-environment1.md)   
 [Windows-Initiated Processing Overview](../HIS2010/windows-initiated-processing-overview1.md)