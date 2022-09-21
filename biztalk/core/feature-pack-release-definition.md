---
title: Step 4 - Create release definitions | Microsoft Docs
description: In Azure DevOps, create a release definition to deploy the BizTalk Server application
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

# Step 4: Create release definition

Like build definitions, release definitions are Azure DevOps tasks, and should probably be done by a Azure DevOps admin. As called out in the Step #3, the build definition builds your project within your git repository, and the release definitions deploys it to your BizTalk Server environment. 


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
      Details: [Create new Biztalk applications](../core/feature-pack-create-application.md)

      - **Update an existing BizTalk Application**: Appends changes, such as schemas, to an already running application. It does not require a full redeploy of the application. 

        Details: [Update a Biztalk applications](../core/feature-pack-update-operation.md)

      - **Install BizTalk Server Application**: Installs the application MSI on the server. 

        Details: [Install a Biztalk applications](../core/feature-pack-install-application.md)

    - **Application Name**: The text you enter will be the application name in BizTalk Administration. Do **not** enter BizTalk Application 1.

    - **Deployment package**: Select the zip file to your application project, and select **OK**. 

8. Select the **Agent phase** task. Select the **Default** Agent queue. **Save** your changes.

9. Select **Release** > **Create release**:  

    :::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-create-release.png" alt-text="Create the release for Azure DevOps in the BizTalk Server project in Visual Studio.":::

10. Select **Queue**. Check the status by clicking the release link. If it fails, the error displays. If it succeeds, the application is added to the BizTalk Administration console. 

## What you did

In VSTS, you created a build definition that builds your application within Git or Team Foundation Version Control (whatever you chose). When changes are made within the source control, the changes are automatically detected, and you can push them. After the build completes, you created a release definition that deploys the application to BizTalk Server, which you can see in BizTalk Server Administration.

## Next steps

At this step, you're done. If you prefer, you can create environmental tokens within your BizTalk XML binding file, and create variables within VSTS that match the environmental tokens. See [Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) for the details. 
