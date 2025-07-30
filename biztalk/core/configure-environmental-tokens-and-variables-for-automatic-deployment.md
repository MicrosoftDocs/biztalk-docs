---
title: Create environmental tokens & variables"
description: Update the binding file to use environment tokens, and create variables in VSTS to automate deployment of BizTalk Server applications
ms.date: "10/19/2020"
ms.reviewer: ""
ms.suite: ""
ms.service: biztalk-server
ms.topic: how-to
ms.custom:
  - "biztalk-2020"
  - sfi-image-nochange
---

# Configure environmental tokens and variables for automatic deployment

Use Visual Studio Team Services (VSTS) variables in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] binding files.

## Overview

In a VSTS environment, you can add variables, and set them to a value. For example, you can create a *sendPortPath* variable, and set its value to a physical folder on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

Within the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] application binding file, the configurable variables can be anything within an XML tag, such as the receive location name, host, send port URI, and so on. 

These variables are specific to your VSTS environment, and can be used to deploy the same application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments. 

We show you how to add the VSTS variable in your binding file, and how to create the variable within VSTS. 

## Add variables to the binding file

1. Open the application binding file:

    :::image type="content" source="./media/configure-environmental-tokens-and-variables-for-automatic-deployment/biztalk-feature-pack-1-binding-1.png" alt-text="Open the BizTalk Server application binding file in Visual Studio.":::

2. Find the element you want to change:

    :::image type="content" source="./media/configure-environmental-tokens-and-variables-for-automatic-deployment/biztalk-feature-pack-1-binding-2.png" alt-text="In the BizTalk Server application binding file, select the element you want to change in Visual Studio.":::

3. Remove the populated value, and replace it with you variables: `$(YourValue)`. For example, enter `$(SendPort1)`: 

    :::image type="content" source="./media/configure-environmental-tokens-and-variables-for-automatic-deployment/biztalk-feature-pack-1-binding-3.png" alt-text="In the BizTalk Server application binding file, remove the existing variable, and change it to your send port variable.":::

4. When done, save the binding file, and add it to your JSON build template (steps in [Step 1: Add Application project & update .json template](feature-pack-add-application-project.md)).

## Create the variables in Azure DevOps

1. In your Azure DevOps account, select **Build and release**, and select **Releases**.

2. Select your **Release definition**, and select **Variables**:  

    :::image type="content" source="./media/configure-environmental-tokens-and-variables-for-automatic-deployment/vsts-release-variables.png" alt-text="Select the release definition and variables in the application binding file in BizTalk Server.":::

3. Select **Add**, and create the variable names and values:

    :::image type="content" source="./media/configure-environmental-tokens-and-variables-for-automatic-deployment/environment-specific-variables.png" alt-text="Add the variables in the BizTalk Server application binding file to Azure DevOps release definition.":::

4. **Save** your changes. When the deploy is initiated, the values are added from the binding file.

## See also

[Configure automatic deployment with Visual Studio Team Services](configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  
