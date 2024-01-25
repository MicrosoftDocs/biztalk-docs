---
title: What is the HIS Designer for Logic Apps
description: Learn about creating mainframe programs and data metadata for Azure Logic Apps by using the HIS Designer for Logic Apps.
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 10/31/2023

#CustomerIntent: As a programmer, I want to learn about creating metadata artifacts for use in Azure Logic Apps using the HIS Designer for Logic Apps.
---

# What is the HIS Designer for Logic Apps? 

To create mainframe and midrange system metadata artifacts for Azure Logic Apps, you can use the Host Integration Server (HIS) Designer for Logic Apps. This tool works with Microsoft Visual Studio and provides a graphical user interface for you to create, view, edit, and map metadata objects to mainframe artifacts. Azure Logic Apps uses these maps to mirror the programs and data in mainframes and midrange systems.

## Why use the HIS Designer?

The mapping capabilities in the HIS Designer tool help Azure Logic Apps workflows access COBOL and RPG programs through the workflow designer. The HIS Designer also reduces the time and effort involved in programming specialized interfaces for mainframe systems by abstracting the complexity managed by a low code platform such as Azure Logic Apps.

## How does the HIS Designer work?
 
In Azure Logic Apps, connectors that access mainframe and midrange systems act as generic proxies by intercepting object method calls from workflows and redirecting them to the appropriate mainframe or midrange program. These connectors also handle the return of all output parameters and values from the mainframe or midrange systems. When the connector intercepts the method call, the connector converts and formats the parameters from the representation understood by the Azure Logic Apps engine into the representation that's understandable by the mainframe transaction program (TP).

You use the HIS Designer to create libraries for use with connectors in Azure Logic Apps. The designer helps you manually create artifacts and import COBOL or RPG definitions called *copybooks*. These copybooks are sections of code that define the data structures of COBOL or RPG programs. Importing copybooks is the most common way to create these objects. There are two types of projects supported by the HIS Designer for Logic Apps: Host Application (for CICS and IMS systems) and Host Files projects (for IBM Host files).

## Downloading the HIS Designer for Logic Apps

You can [download and install the HIS Designer for Logic Apps from the Download Center](https://aka.ms/his-designer-logicapps-download). The only prerequisite is [Microsoft .NET Framework 4.8](https://aka.ms/net-framework-download).

## Next steps

> [!div class="nextstepaction"]
> [Designing Metadata Artifacts for Host Applications (CICS/IMS)](application-integration-lahostapps.md)

> [!div class="nextstepaction"]
> [Designing Metadata Artifacts for Host Files](application-integration-lahostfiles.md)

> [!div class="nextstepaction"]
> [Designing Metadata Artifacts for 3270 Applications](application-integration-la3270apps.md)
