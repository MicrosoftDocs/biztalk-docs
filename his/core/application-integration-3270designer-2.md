---
title: What is the 3270 Design Tool
description: Get started with the 3270 Design Tool for Azure Logic Apps. This development tool helps you create green-screen applications.
author: haroldcampos
ms.author: "hcampos"
ms.prod: "host-integration-server"
ms.topic: overview 
ms.date: "10/17/2023"

#CustomerIntent: As a programmer, I need to create metadata for the 3270 connector in Azure Logic Apps using the 3270 Design Tool.
---

# What is the 3270 Design Tool? 

Learn how to create mainframe metadata for 3270 stream-based artifacts to use in Azure Logic Apps.

## What is the 3270 Design Tool

The 3270 Design Tool is a desktop application used to define metadata used by the IBM 3270 Connector for Azure Logic Apps to navigate and interact with your 3270 applications.

:::image type="content" source="media/la-3dtdesigner-main-view1.png" alt-text="HIS Designer for Logic Apps":::

## Why do we need a Tool for interacting with 3270 Applications?

In a 3270 screen-driven app, the screens and data fields are unique to your scenarios, so the 3270 connector needs this information about your app, which you can provide as metadata. This metadata describes information that helps your logic app identify and recognize screens, describes how to navigate between screens, where to input data, and where to expect results. To specify and generate this metadata, you use the 3270 Design Tool, which walks you through these specific modes, or stages, as described later in more details.

## How does it work?

In a 3270 screen-driven app, the screens and data fields are unique 
to your scenarios, so the 3270 connector needs this information about 
your app, which you can provide as metadata. This metadata describes 
information that helps your logic app identify and recognize screens, 
describes how to navigate between screens, where to input data, 
and where to expect results. To specify and generate this metadata, 
you use the 3270 Design Tool, which walks you through these specific 
*modes*, or stages, as described later in more details:

* **Capture**: In this mode, you record the screens required for completing 
a specific task with your mainframe app, for example, getting a bank balance.

* **Navigation**: In this mode, you specify the plan or path for how 
to navigate through your mainframe app's screens for the specific task.

* **Methods**: In this mode, you define the method, for example, 
`GetBalance`, that describes the screen navigation path. You also 
select the fields on each screen that become the method's input 
and output parameters.

## Unsupported elements

The design tool doesn't support these elements:

* Partial IBM Basic Mapping Support (BMS) maps: If you import a BMS map, the design tool ignores partial screen definitions.

* Menu processing

## Downloading the 3270 Design tool

The HIS Designer for Logic Apps can be downloaded from the Download Center.

## Next step

> [!div class="nextstepaction"]
> [Designing Metadata Artifacts for 3270 Applications](application-integration-la3270apps.md)
