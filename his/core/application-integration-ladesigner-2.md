---
title: "What is the HIS Designer for Logic Apps | Microsoft Docs"
description: Get started with the HIS Designer for Logic Apps, development tool available for creating mainframe programs and data metadata for Azure Logic Apps  
author: haroldcampos
ms.author: "hcampos"
ms.prod: "host-integration-server"
ms.service: #Required; use the name-string related to slug in ms.product/ms.service
ms.topic: overview #Required; leave this attribute/value as-is.
ms.date: "10/03/2023"

#CustomerIntent: As a programmer, I need to create metadata artifacts for use in Azure Logic Apps using the HIS Designer for Logic Apps.
---

# What is the HIS Designer for Logic Apps? 

Learn how to create Mainframe and Midranges metadata artifacts for Azure Logic Apps.
The Host Integration Server (HIS) Designer for Logic Apps is a tool that works with Microsoft Visual Studio to provide a graphical user interface for creating, viewing, and editing metadata objects that map to Mainframe artifacts. These maps are used by the Azure Logic Apps to mirror programs and data of the Mainframes and Midranges.

:::image type="content" source="media/la-designer-main-view1.png" alt-text="HIS Designer for Logic Apps":::

## Why do we need a Designer?

The Mapping capabilities provided by the HIS Designer tool, allow the Logic Apps workflows to access COBOL and RPG programs leveraging the capabilities of the Logic Apps Designer. The use of the HIS Designer for Logic App also reduces the time and effort involved in programming specialized interfaces for mainframe systems by abstracting the complexity managed by a Low Code platform such as Azure Logic Apps.

## How does it work?
 
Our Logic Apps connectors for Mainframes and Midranges systems act as generic proxies, by intercepting object method calls from Logic Apps and redirecting them  to the appropriate Mainframe or Midrange program. The connectors also handle the return of all output parameters and values from the mainframe systems. When the connector intercepts the method call, it converts and formats the parameters from the representation understood by the Logic Apps engine into the representation that is understandable by the mainframe transaction program (TP).
The HIS Designer for Logic Apps is used to create libraries for use with the Logic Apps connectors. It allows the manual creation of artifacts and also importing COBOL or RPG definitions called Copybooks. Copybooks are sections of code that define the data structures of COBOL or RPG programs. Importing copybooks is the most common way to create these objects. There are two types of projects supported by the HIS Designer for Logic Apps: Host Application (for CICS and IMS systems) and Host Files projects (for IBM Host files).

## Downloading the HIS Designer for Logic Apps

The HIS Designer for Logic Apps can be downloaded from the Download Center.

## Next step

> [!div class="nextstepaction"]
> [Designing Metadata Artifacts for Host Applications (CICS/IMS)](application-integration-lahostapps.md)

> [!div class="nextstepaction"]
> [Designing Metadata Artifacts for Host Files](application-integration-lahostfiles.md)

> [!div class="nextstepaction"]
> [Designing Metadata Artifacts for 3270 Applications](application-integration-la3270apps.md)