---
title: "Localities and DMODs (SNADIS)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69cd51f0-5281-4f26-b07e-55950c722d37
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Localities and DMODs (SNADIS)
A Base and its components (that is, a [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] executable program) is called a **locality**. The Host Integration Server system therefore consists of one or more communicating localities (all the running [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] executable programs within the LAN Manager domain). For each Host Integration Server system, there is a central configuration file. In addition, each Host Integration Server computer maintains configuration information about the SNALinks it supports.  
  
 In a system such as Host Integration Server, where the number of localities and their types are not configured in advance, the relationships between the localities are set up dynamically as individual localities come and go. Localities that can enter and leave a system in this way are called **dynamic localities**.  
  
 Dynamic localities communicate using the Dynamic Access Module (DMOD) component, which provides the communications facilities needed to pass messages between the Bases. This is illustrated in the following figure.  
  
 ![](../core/media/his-32701a.gif "his_32701a")  
Dynamic localities communicating using the DMOD component  
  
 This figure shows a system consisting of three dynamic localities. Dynamic localities can enter or leave this system at any time.