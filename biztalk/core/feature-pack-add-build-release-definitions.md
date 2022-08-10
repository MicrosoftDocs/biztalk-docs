---
title: Step 3 - Create the build and release definitions | Microsoft Docs
description: In VSTS, create a build definition to build the projects within your git or TFS repository, then create a release definition to deploy the BizTalk Server application
ms.custom: ""
ms.date: "12/15/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
author: MandiOhlinger
ms.author: mandia
manager: "anneta"
---

# Step 3: Create the build and release definition

The build and release definitions are Azure DevOps tasks, and should probably be done by a Azure DevOps admin. The build definition builds your project within your git repository, and the release definitions deploys it to your BizTalk Server environment. 

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

## Add the release tasks

When the build succeeds, the release definition deploys your application to your BizTalk Server. 

1. Select the **Releases** tab > **New pipeline**. 

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-new-pipeline.png" alt-text="Create a new pipeline as a release task for Azure DevOps in the Visual Studio BizTalk Server project.":::

2. Select the **Empty** template > **Apply**:

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-empty-release-template.png" alt-text="Add an empty pipeline template as a release task for Azure DevOps in the Visual Studio BizTalk Server project.":::

3. Change the **Environment name** to **Dev**, or whatever you want to call it. 

4. Select **Add artifact**, select your project, your build definition, and select **Add**: 

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-add-artifact.png" alt-text="Add an artifact to the pipeline, and choose your project and build definition for Azure DevOps in the Visual Studio BizTalk Server project.":::

5. Go to the **Tasks** tab, add a new task: 

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-new-release-tasks.png" alt-text="Add a task to the pipeline release for Azure DevOps in the Visual Studio BizTalk Server project.":::

6. From the list, filter the results, select the **BizTalk Server Application Deployment** task > **Add**:  

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-biztalk-application-deployment-task.png" alt-text="Add a BizTalk Server application eeployment task to the pipeline release for Azure DevOps.":::

    If **BizTalk Server Application Deployment** isn't listed, then install it at [Deploy BizTalk Application](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).

7. Select the **Deploy** task, and enter the values:

    - **Operation Name**: Your options:

      - **Create new BizTalk Application**: Deploys a new application. If the application already exists, it uninstalls the current applications (full stop), and installs the new application. If continuous integration is enabled, it automatically redeploys the application when it is updated in the repository.   
      - **Update an existing BizTalk Application**: Appends changes, such as schemas, to an already running application. It does not require a full redeploy of the application.  
      - **Install BizTalk Server Application**: [Install the applications](../core/how-to-install-a-biztalk-application.md). You enter the Application Name. Make sure that the application is installed in the same Biztalk Server group where installation is being done.  

        :::image type="content" source="./media/feature-pack-add-build-release-definitions/vsts-deploy-operations.png" alt-text="Install the BizTalk Server application as a deployment task for Azure DevOps in Visual Studio.":::

        - **Application Name**: Name of the application that needs to be installed.

    - **Deployment package**: Select the zip file to your application project, and select **OK**. 

8. Select the **Agent phase** task. Select the **Default** Agent queue. **Save** your changes.

9. Select **Release** > **Create release**:  

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-create-release.png" alt-text="Create the release for Azure DevOps in the BizTalk Server project in Visual Studio.":::

10. Select **Queue**. Check the status by clicking the release link. If it fails, the error displays. If it succeeds, the application is added to the BizTalk Administration console. 

## What you did

In VSTS, you created a build definition that builds your application within Git or Team Foundation Version Control (whatever you chose). When changes are made within the source control, the changes are automatically detected, and you can push them. After the build completes, you created a release definition that deploys the application to BizTalk Server, which you can see in BizTalk Server Administration.

## Next steps

At this step, you're done. If you prefer, you can create environmental tokens within your BizTalk XML binding file, and create variables within VSTS that match the environmental tokens. See [Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) for the details. 
