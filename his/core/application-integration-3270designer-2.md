---
title: What is the 3270 Design Tool
description: Learn about creating green-screen applications with the 3270 Design Tool for Azure Logic Apps.
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 10/17/2023

#CustomerIntent: As a programmer, I need to create metadata for the 3270 connector in Azure Logic Apps using the 3270 Design Tool.
---

# What is the 3270 Design Tool? 

To create mainframe metadata for 3270 stream-based artifacts to use in Azure Logic Apps, you can use the 3270 Design Tool. This tool is a desktop application that helps you define metadata used by the IBM 3270 connector in Azure Logic Apps to navigate and interact with your 3270 applications.

:::image type="content" source="media/la-3dtdesigner-main-view1.png" alt-text="HIS Designer for Azure Logic Apps":::

## Why use the 3270 Design Tool to interact with 3270 applications?

During the prevalence of System Network Architecture (SNA), the 3270 data stream was used as the display management protocol that facilitated communication between remote end users and a centralized mainframe. A device known as a 3270 terminal existed in an SNA network at the end user's location.

Due to many SNA and 3270 applications existing at that time, customers looked at integrating their SNA protocol into their IP backbone. They used a technology known as Telnet 3270 (TN3270) to move from SNA 3270 applications to TCP/IP. For more information, see [Introduction to the 3270 terminal](https://www.ibm.com/docs/en/zos-basic-skills?topic=enhanced-introduction-3270-terminal).

3270 applications are pervasive in IBM mainframe environments. To access these applications, which often have business logic embedded with the screens, separating the screen and business logic might not be possible, or maybe you no longer have information for how the applications work. The 3270 Design Tool helps parse and process these applications so that you can reuse the screen information.

## How does the 3270 Design Tool work?

In a 3270 screen-driven app, the screens and data fields are unique to your scenarios, so the 3270 connector needs this information about your app, which you can provide as metadata. This metadata describes information that helps your logic app identify and recognize screens, describes how to navigate between screens, where to input data, and where to expect results. To specify and generate this metadata, you use the 3270 Design Tool, which walks you through these specific *modes*, or stages, as described later in more details:

* **Capture**: In this mode, you record the screens required for completing a specific task with your mainframe app, for example, getting a bank balance.

* **Navigation**: In this mode, you specify the plan or path for how to navigate through your mainframe app's screens for the specific task.

* **Methods**: In this mode, you define the method, for example, `GetBalance`, that describes the screen navigation path. You also select the fields on each screen that become the method's input and output parameters.

## Unsupported elements

The design tool doesn't support partial IBM Basic Mapping Support (BMS) maps. If you import a BMS map, the design tool ignores partial screen definitions.

## Downloading the 3270 Design tool

You can [download the 3270 Design Tool from the Download Center](https://www.microsoft.com/download/details.aspx?id=57962).

## Next step

> [!div class="nextstepaction"]
> [Designing metadata artifacts for 3270 applications](application-integration-la3270apps.md)
