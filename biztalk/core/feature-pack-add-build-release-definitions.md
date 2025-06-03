---
title: Step 3 - Create the build definitions
description: In Azure DevOps, create a build definition to build the projects within your git or TFS repository
ms.custom: ""
ms.date: "9/20/2022"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---

# Step 3: Create the build definition

The build and release definitions are Azure DevOps tasks, and should probably be done by an Azure DevOps admin. The build definition builds your project within your git repository, and the release definitions deploys it to your BizTalk Server environment. 

## Before you begin

Complete [Step 2 - Create Azure DevOps token and install agent](feature-pack-create-vsts-token.md).

## Add the Build tasks

1. In your project, select **Pipelines** > **Create Pipeline**:

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-pipeline.png" alt-text="Create a new pipeline project in BizTalk Server.":::

    Use the classic editor to create a pipeline without YAML:

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-create-pipeline.png" alt-text="Use the classic editor without YAML to create a new pipeline in BizTalk Server.":::

    Select **Azure Repos Git** > **Continue**:

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-repos-git.png" alt-text="Select Azure repos git to host your new pipeline in BizTalk Server.":::

2. Select the **Empty** template > **Apply**:  

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-empty-template.png" alt-text="Select the empty template to create a new pipeline in BizTalk Server.":::

3. Set the **Agent Pool**. Your options:

    - **Azure Pipelines**: Select this option to use Azure hosted agents > **windows-2019**:

        :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-azure-pipelines.png" alt-text="Select the Azure Pipelines for the agent pool in Azure DevOps and BizTalk Server.":::

    - **Default**: Select this option to use your own defined agent pool:

        :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-select-agent-queue.png" alt-text="Select the default queue for the agent pool in Azure DevOps and BizTalk Server.":::

4. In **Phase 1**, add a task, select **Visual Studio Build** > **Add**:

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-add-visual-studio-task.png" alt-text="Add a Visual Studio build task to your BizTalk Server project.":::

5. Select the Visual Studio Build task you just added, and set the following properties:

    - **Display name**: Enter your build solution, such as `YourProjectName/YourProjectName.sln`.
    - **Visual Studio version**: Select at least Visual Studio 2015. You can also select **Latest**.
    - **MSBuild Architecture**: Select **MSBuild x86**.

    Your properties look similar to the following:

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-repos-build-properties.png" alt-text="Sample Visual Studio build properties in your BizTalk Server project.":::

6. In **Phase 1**, add a task, select **Publish Build Artifacts** > **Add**:

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-add-publish-build-task.png" alt-text="Add a Visual Studio build artifacts task to your BizTalk Server project.":::

7. Select the **Publish Artifact** task, and enter your preferred **Display name**. For **Path to publish**, select the **...**  button, and choose the application project folder (e.g. appProjectHelloWorld). Select **OK**.

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-publish-artifacts.png" alt-text="Select the publish artifacts task in your Visual Studio BizTalk Server project.":::

8. The **Artifact Name** can be anything you want. Select **Save**. 

9. Go to **Triggers**, and set the **Trigger status** to **Enabled**:  

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-continuous-integration.png" alt-text="Add and enable a Visual Studio trigger to your BizTalk Server project.":::

10. **Save & Queue** to test your build definition. When you queue, you are prompted for the agent queue and your branch. Select the **Default** agent queue, and choose your branch. Select **Queue**.  

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-run-pipeline.png" alt-text="In run pipeline, add the aqent queue and Azure DevOps branch in the Visual Studio BizTalk Server project.":::

11. A new build is started, and you can select it to check for a success or failure. 



## What you did

In Azure DevOps, you created a build definition that builds your application within Git or Team Foundation Version Control (whatever you chose). When changes are made within the source control, the changes are automatically detected, and you can push them. 

## Next steps

[Step 4: Create the release definition](azure-devops-add-release-definition.md)  
[Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md)
